---
sidebar_position: 7
---

# HttpMessageConverter 的配置

场景：部分项目需要自定义MessageConverter， 集成过程中需要排除海牛工作台所需的接口。 避免影响到项目的正常运行。

第一步：创建自定义HttpMessageConverter类； 代码如下：
```java


import org.apache.commons.lang3.StringUtils;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.http.HttpInputMessage;
import org.springframework.http.MediaType;
import org.springframework.http.converter.HttpMessageNotReadableException;
import org.springframework.http.converter.json.MappingJackson2HttpMessageConverter;
import org.springframework.web.context.request.RequestContextHolder;
import org.springframework.web.context.request.ServletRequestAttributes;

import javax.servlet.http.HttpServletRequest;
import java.io.IOException;
import java.lang.reflect.Type;
import java.util.ArrayList;
import java.util.List;

public class ManateeMappingJacksonHttpMessageConverter extends MappingJackson2HttpMessageConverter {

    private static final Logger LOGGER = LoggerFactory.getLogger(ManateeMappingJacksonHttpMessageConverter.class);

    /**
     * 不需要过滤的host
     */
    protected static List<String> hosts;
    static {
        hosts =  new ArrayList<>();
        hosts.add("http://xxx.xxx.xx.xx:xxxx");//这里将工作台的域名/ip+端口地址添加进去
    }


	//重写该方法，我们只需要加上Object tempObj = this.process( obj, type, inputMessage );
    //并返回tempObj,process方法里面我们过滤白名单处理
    @Override
    public Object read(Type type, Class<?> contextClass, HttpInputMessage inputMessage) throws IOException,
            HttpMessageNotReadableException {
        HttpServletRequest request = ((ServletRequestAttributes) (RequestContextHolder.currentRequestAttributes())).getRequest();
        if (this.isNeedProcess(request)) {
            return super.read(type, contextClass, inputMessage);
        }
        MappingJackson2HttpMessageConverter jackson2HttpMessageConverter =
                new MappingJackson2HttpMessageConverter();
        return jackson2HttpMessageConverter.read(type, contextClass, inputMessage);
    }


    @Override
    public boolean canRead(Class<?> clazz, MediaType mediaType) {
        HttpServletRequest request = ((ServletRequestAttributes) (RequestContextHolder.currentRequestAttributes())).getRequest();
        boolean canRead = super.canRead(clazz, mediaType);
        if (canRead) {
            return isNeedProcess(request);
        }
       return canRead;
    }

    @Override
    public boolean canWrite(Class<?> clazz, MediaType mediaType) {
        HttpServletRequest request = ((ServletRequestAttributes) (RequestContextHolder.currentRequestAttributes())).getRequest();
        boolean canWrite = super.canWrite(clazz, mediaType);
        if (canWrite) {
            return isNeedProcess(request);
        }
        return canWrite;
    }

    //根据白名单，判断当前请求路径是否需要过滤
    protected boolean isNeedProcess(HttpServletRequest request) {

        String requestURI = request.getRequestURI();
        try {
            //根据白名单做下匹配，当然也可以实现正则什么的
            String host = request.getHeader("Origin");
            String lowcodeToken = request.getParameter("lowcodeToken");
            String debug = request.getParameter("debug");
            if ("TRUE".equalsIgnoreCase(debug)) {
                return true;
            }
            boolean isWangFaWork = StringUtils.isNotBlank(lowcodeToken) || hosts.contains(host);
            if (isWangFaWork) {
                return false;
            }
        } catch (Exception e) {
            LOGGER.error("isNeedProcess error, CanonicalName:{}, 转换处理处理-url处理失败,requestURI={}, e:{}", this.getClass().getCanonicalName(), requestURI, e);
            return true;
        }

        return true;


    }
```

第二步，替换WebMvcConfigurer原有声明的 MessageConverter
```java
    @Override
    public void configureMessageConverters(List<HttpMessageConverter<?>> converters) {
        WebMvcConfigurer.super.configureMessageConverters(converters);

    	// 此处使用新的 MessageConverters 即可
        ManateeMappingJacksonHttpMessageConverter jackson2HttpMessageConverter =
                new ManateeMappingJacksonHttpMessageConverter();

        // 所有的自定义配置可以保持原来的配置不用变
        ObjectMapper objectMapper = new ObjectMapper();
        SimpleModule simpleModule = new SimpleModule();
        simpleModule.addSerializer(Long.class, ToStringSerializer.instance);
        simpleModule.addSerializer(Long.TYPE, ToStringSerializer.instance);
        objectMapper.registerModule(simpleModule);
        jackson2HttpMessageConverter.setObjectMapper(objectMapper);

        converters.add(0, jackson2HttpMessageConverter);
    }

```
 
