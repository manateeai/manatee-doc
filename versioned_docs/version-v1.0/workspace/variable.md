---
sidebar_position: 5
---

# 变量

## 在组件的配置里，时常会看到两种类型的输入框：
第一种：有带“变量”标识
第二种：没有"变量"标识
它们的区别这样的：
在所有带“变量”标识的地方，填入的是变量名，实际使用的是该变量的值。
在没有"变量"标识的地方，填入的内容就是实际使用的内容。

## 之所以这样设计是因为：
	直接使用变量更简单和符合开发习惯，使用函数时也更直观(使用函数时不可用${}取值)。
	但工作台中并非所有的输入框都是为了取变量，比如：结果对象名、数组对象名、日志信息等，这些地方大多数情况下都是为了直接使用填入的内容，不需要使用变量。
	而填使用内容的这些地方，小部分情况也有变量替换的需求，
	比如：
		日志信息，要打印出：XXX操作成功。xxx需要动态替换
		这时候可以在文本中使用${} 来达到效果：${xxx}操作成功。

	因此总结一下：
		**在所有含有“变量”标识的地方，是直接使用变量。**
**		而${}的使用场景和能力范围在于：字符串内容替换，即字符串和变量拼接的场景。 **

	尽管在一些直接使用变量的地方使用${}也可以实现一样效果，如在数据处理里这样写：msg = ${name}也是把name的值赋给了msg，这样写等同于java里的 new StringBuilder(name),把name作为字符串用来拼接，只不过拼接的只有name一个值而已，然后把得到的赋值给msg。

	因此**官方推荐优先按照建议的方式使用变量和${}：在所有带“变量”标识的地方直接写变量名，仅在字符串拼接变量的场景使用${}**。这样会更方便和稳定。
[
](https://oss.manateeai.com/juzhun/bianliangquzhi.mov)
直接使用变量视频案例
[https://oss.manateeai.com/juzhun/bianliangquzhi.mov](https://oss.manateeai.com/juzhun/bianliangquzhi.mov)

${}取变量视频案例
[https://oss.manateeai.com/juzhun/fuhaoquzhi.mov](https://oss.manateeai.com/juzhun/fuhaoquzhi.mov)

Mac OS 可以使用 Safari 浏览器进行播放。


