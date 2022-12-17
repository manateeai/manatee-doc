---
sidebar_position: 6
---
# 与 jeecg 配合使用

## online 开发模式
jeecg 的 online 开发可以零代码配置出通用的增删改查接口，但是如果有需要特殊处理的业务逻辑，则要通过写代码来实现，然后通过 jeecg 的增强机制和功能关联起来。
这部分要特殊处理的业务逻辑，则可以通过海牛来快速开发，然后通过 jeecg 的增强机制和生成的功能结合起来。

1. 海牛项目配置
    1. 工作台项目返回结构配置

![jeecg 海牛_1.png](img/jeecg 海牛_1.png)
2. 海牛 controller 替换为此 controller[ModularityController.java](https://www.yuque.com/attachments/yuque/0/2022/java/12452833/1663594443155-1ef76146-898a-433c-aa23-8bc53693dc37.java?_lake_card=%7B%22src%22%3A%22https%3A%2F%2Fwww.yuque.com%2Fattachments%2Fyuque%2F0%2F2022%2Fjava%2F12452833%2F1663594443155-1ef76146-898a-433c-aa23-8bc53693dc37.java%22%2C%22name%22%3A%22ModularityController.java%22%2C%22size%22%3A10282%2C%22type%22%3A%22%22%2C%22ext%22%3A%22java%22%2C%22source%22%3A%22%22%2C%22status%22%3A%22done%22%2C%22mode%22%3A%22title%22%2C%22download%22%3Atrue%2C%22taskId%22%3A%22u041147d4-44ee-4b11-be42-5f00ea79b84%22%2C%22taskType%22%3A%22upload%22%2C%22__spacing%22%3A%22both%22%2C%22id%22%3A%22u0df351bc%22%2C%22margin%22%3A%7B%22top%22%3Atrue%2C%22bottom%22%3Atrue%7D%2C%22card%22%3A%22file%22%7D)

2. 开发海牛接口

如果参数是单条记录（如新增/编辑的时候），参数 key 为 record，如果有返回值，则需返回更改后的 record。
如果参数是多条记录（如查询的时候），参数 key 为 dataList，如果有返回值，则需将更新后的 dataList 命名为 result。

3. 选择 Java 增强

![jeecg 海牛_2.png](img/jeecg 海牛_2.png)

4. 选择 http-api 模式，内容填入海牛接口路径

![jeecg 海牛_3.png](img/jeecg 海牛_3.png)

## 代码生成模式
方式一：引入 ModularityManager，用 modularityManager 调用海牛流程图
```java
@Autowired
private ModularityManager modularityManager;
```
![jeecg 海牛_4.png](img/jeecg 海牛_4.png)
方式二：用海牛开发后端接口。


