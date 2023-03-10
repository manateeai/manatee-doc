---
sidebar_position: 2
---
# 组件扩展

## 依赖
```xml
        <dependency>
            <groupId>com.manatee.manatee-lowcode</groupId>
            <artifactId>common-util</artifactId>
            <version>${lowcode-all.version}</version>
        </dependency>

        <dependency>
            <groupId>com.manatee.manatee-lowcode</groupId>
            <artifactId>lowcode-core</artifactId>
            <version>${lowcode-all.version}</version>
        </dependency>
```

### Api 说明
获取上下文中的字符串内容：
content.getStepConfString(key);

获取上下文中的字符串内容，若字符串中含有${xxx},则替换xxx为其对应的变量值：
variableUtil.calVarInConf(content,key);

获取上下文中变量值:
content.getValue(key);

获取数据处理后内容(当handleType为batch时，获取批量数据处理后的结果):
inputUtil.getHandleObject(content,Key);

设置默认返回值的对象名:
outputUtil.setDefaultReturnKey(content,defaultReturnKey);

对内容进行数据处理:
inputUtil.getHandleMapConf(content, queryParamsObj);

把数据放入返回, 默认对象名为outputData：
outputUtil.putData (content,value );

数据处理并放入返回, 默认对象名为outputData:
outputUtil.handleAndPutData(content,value );

抛出异常：
 		throw new BizException(ResultCode._SYSTEM_ERROR_,"params is not json");

## 服务端实现

实现接口 IProcess，重写其方法，在类上加注解 @Service (注意：确保该类在项目spring的扫描目录下)，重启当前项目，即可在工作台中使用该组件。


演示例子，更多案例可以从manatee-lowcode查看：
```java
@Service
public class DemoProcess implements IProcess {

    @Resource
    protected IOutputUtil outputUtil;

    @Resource
    private VariableUtil variableUtil;

    @Override
    public void process(ProcessContent content) throws BizException{
        String name = variableUtil.calVarInConf(content,"name");
        String result = "hello "+name;
        outputUtil.putData(content,result);
    }

    @Override
    public String getName() {
        return "demoProcess";
    }
```

IProcess方法说明
String getName();
组件唯一标识，如：mysqlQueryProcess

void process(ProcessContent content);
组件执行逻辑，用户在此方法内实现组件功能。

可能要引入的类
```java
    @Resource
    protected IInputUtil inputUtil;

  	@Resource
    protected IOutputUtil outputUtil;

    @Resource
    private VariableUtil variableUtil;

```

## 配置组件页面
![组件扩展_1.png](img/组件扩展_1.png)
注意：英文名称需要和代码里getName方法返回内容一致。
