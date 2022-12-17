### Installation
1. make sure nvm installed
2. install node v16.14 by 
```
nvm install 16.14
```
3. use node v16.14
```
nvm use v16.14
```
4. install yarn
```
npm install --global yarn
```

4. install dependence

```
$ yarn
```

### Local Development

```
$ yarn start
```

This command starts a local development server and opens up a browser window. Most changes are reflected live without having to restart the server.


### Write Document
total markdown features:
https://docusaurus.io/docs/markdown-features

markdown front matter:
https://docusaurus.io/docs/api/plugins/@docusaurus/plugin-content-docs#markdown-front-matter


**要求**
1. 中文中间出现英文或数字的的，英文或数字前后要加空格
2. 注意标准名词的使用：
    * MySQL
    * Java

**Tips**

1. 如果写文档的时候，觉得某处需要链接到另外一个文档进一步详细说明，但这个文档还没有，可以先用 [文字文字-链接] 这样的代替，回头可以统一查漏补缺。

2. 为了让文档 url 是更规范的全英文，也为了以后中英文版本文档可以相互切换，.md 文档文件名用英文命名，文档内最开头放一个唯一的一级标题。参考 [这个文档](./versioned_docs/version-v1.0/update/workspace-change-log.md)

### Build

```
$ yarn build
```

This command generates static content into the `build` directory and can be served using any static contents hosting service.