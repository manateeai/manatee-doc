---
sidebar_position: 11
---
### 适合哪些公司，目标客户？
对行业没有特别要求，我们目前沉淀的是一套通用的解决方案，适合对软件开发比较频繁的企业和项目。
当项目比较多、需求比较多的时候，更能体现低代码的优势，起到很好的复用，减少大量编码，大大提高维护性。

### 你们和现在低代码方案有什么区别？
海牛现在主要服务有研发团队的企业，这些企业的系统复杂度和要求是比较高的。

市面上其他的低代码产品，只适用于一小部分固定场景，而且灵活度很低，这些产品适合简单通用、逻辑不多的场景，一些复杂多变的需求基本不是这类产品可以做的，不然，研发团队就不需要那么多人了。而用海牛的话，只要 Java 能实现的，海牛就能实现（也可以海牛 Java 一起用，无缝衔接），且效率比 Java 开发高很多。

海牛以模块化架构为起点，相继推出了组件、函数、场景、自动化文档、自动化测试...，深入开发的各个环节里提高效率，尤其是在开发和维护上，效果会特别明显。
### 对于公司内部有老项目，如何做？

1. 是否对老系统有影响？

    老项目升级是轻量级的，只是接入了海牛的 jar 包，老的代码接口不会有任何影响，项目的部署方式和原来一样，写代码开发都是可以的，和老系统完美融合。

2. 老系统重构，对于老系统重构成本极其高。海牛提供了方案：
    * 对老系统进行升级成模块化，这样新开发的需求都可以模块化，让老系统不会继续复杂。
    * 后面通过蚂蚁搬家的方式把老系统慢慢重构成模块化，一段时间之后系统变得更轻量级。

老项目时间越久维护成本越大、人效越低，引入海牛以后，老项目现有的东西不会受到任何影响。老项目里的新需求用海牛去开发可以把人效大幅提升几倍。而且海牛也不是绑架式的集成，在一个需求里开发者可以自由选择是用海牛、还是用老代码方式、或者两者搭配使用。海牛是给了开发者一种选择，让他们在面对难以维护的老项目时，有一种高效的开发方式能选择。

### 公司内部已经有成熟系统，小海牛方案能帮助这类系统吗？

可以。

针对已经有成熟系统的企业，小海牛提供和原有系统融合的方案，及我们提供核心 Jar 包，原有系统只要依赖就拥有低代码开发能力，并且通过“本地调用”组件，可以调用原来写的代码，不用从 0 开始。
特点：当原有系统轻量级地引入低代码方案后，新的需求可以用积木化的方式搭建，以后项目中更多的功能可以沉淀更多的业务组件，使目前系统的架构逐渐优化。

### 方便排查问题吗？
开放组件源码，还是程序员熟悉的排查方式，同时开发工作台支持智能调试，智能定位问题。

### 对实习生初级开发者是否友好？
对于实习生而言很多公司采取的是先拿一些简单项目让其练手，逐渐熟练以后进入复杂开发。小海牛平台并没有跳过实习生的成长过程，而是以一种更高效的方式加速这个过程。

众所周知，程序员的资深与否在于其对业务对理解能力，和娴熟的抽象能力、逻辑能力，小海牛平台节约掉大部分的“无脑搬砖”时间，进而让程序员聚焦于业务的抽象和设计实现。

而且，小海牛平台并不是“零代码”，其开放式的扩展能力，需要程序员在工作过程中遇到某些可以复用的功能或者业务时，对其进行封装，输出到平台上，进而使整个公司其他同事再遇到相同问题时可以直接复用。


### 程序员如何成长？
赋能普通程序员，减少重复开发的时间，更多的精力用来设计和思考业务和开发更高质量组件或模块，更好地创造和思考业务架构思想和规范，帮助普通程序员以资深开发和架构师的高度思考，助力成长。


### 性能对比 Java 代码怎么样？
从执行过程来说，海牛模块化和 Java 代码执行对比，主要多了一步读取配置信息和路由结构，这部分会加载在内存中，读取内存中的配置信息，并根据配置信息执行 Java bean 代码，和原来直接代码执行来说耗时在 0.5ms 以内，可以忽略不计，执行部分都是调用 Java bean 来执行；

另外对于数据库，如 MySQL 场景中，通过压测，海牛调用数据库耗时是传统 mybatis 的 80%，mybatis 封装的比较多，我们直接是通过 jdbc 实现的，并且做了一些优化执行，在 IO 比较多的场景中效果会更明显。

对于性能调优，因为组件源码都是用 Java 代码实现的，且组件代码都是开放的，研发可以对其进行调优。平台推荐的方式也是由资深人员统一封装、维护和调优组件，然后其他人去使用组件即可。

### 该方案稳定性如何？是否能支撑我们目前业务？
目前方案是一套成熟的解决方案，雏形阶段服务于淘宝内部会员平台，每秒处理 5 万+数据量级，服务于淘抢购、淘宝会员、闲鱼等内部 10 多个业务部门，帮助这些部门落地了会员解决方案，以及一些在阿里内部复杂度很高的场景，甚至包括一些涉及红包和资金的场景（淘抢购），再后来用于场景更复杂的美港股金融大数据量化回测模型分析中。

业务的风险来说，我们本质上是一种组件化开发方式，我们会提供精心打磨的基础组件，具备非常强的扩展能力（我们提供了灵活和可视化的组合方式），组件经过了多个项目和使用，稳定度非常高，我们引导开发者去开发自己的组件（对现有人员更高的抽象要求），当我们实现一个业务需求的时候，如果能大量复用原来的被大量测试的代码，bug 数，风险都会大量减少。我们本质上是给现有开发人员赋能，让他能更高效的产出。

### 如果小海牛业务变更了，会影响我们使用吗？
我们目前输出的是一整套解决方案，纯私域化部署，整个运行不依赖于小海牛公司，如果小海牛业务变更了，不会影响公司使用，而且我们提供大部分源码，用户可以在我们基础上迭代升级。

### 安全性如何，我们数据代码是否会泄露，是否有后门，是否会有安全漏洞？

1. 我们是纯私域化部署，不会有任何外部调用，代码数据都属于公司内部；
2. 我们是白盒，预制件源码开放（核心引擎变量混淆，代码开发），可以清楚看到是怎么运行的、是否留后门，当然海牛不会留任何后门；
3. 目前有安全类上市公司签约并内部大规模使用，对我们进行了极其严格的安全测试。

**您还有哪些关心的问题，可以随时向工作人员提出，我们将及时回应**