---
sidebar_position: 1
---
# 引擎更新日志
## 3.9.12 版本（2022 年 09 月 23 日）

### 修复
* 级联查询结果不是 list
* 排除处理中过程字段输入框：字段名之间有空格排除不掉

### 下载地址
[引擎包 3.9.12](https://manateeai.oss-cn-hangzhou.aliyuncs.com/deploy/%E5%BC%95%E6%93%8E%E5%8E%86%E5%8F%B2%E7%89%88%E6%9C%AC/3.9.12_manatee.zip)

---

## 3.9.11 版本（2022 年 08 月 30 日）

### 新增
* 读取项目配置函数：getSpringProperties("xxx.xx")
* 三方脚本 js、groovy、python 等组件
* TCP/UDP
* WebSocket 组件
* 文件解压缩组件
### 优化
* 优化级联查询支持反向级联 
### 修复
* 修复级联查询字段名大写报错
* 修复关联表查询字段中间有空格会报错 
* 修复自定义函数（randomNumbers，format）嵌套问题 
* 修复 select 里有嵌套的情况并使用 orderby 同时打开返回总记录数会报错 
* 修复接口返回数据格式不对  


### 下载地址
[引擎包 3.9.11](https://manateeai.oss-cn-hangzhou.aliyuncs.com/deploy/%E5%BC%95%E6%93%8E%E5%8E%86%E5%8F%B2%E7%89%88%E6%9C%AC/3.9.11_manatee0901.zip)

---

## 3.9.10 版本（2022 年 08 月 11 日）

### 3.9.10_hotfix_0823
* **修复**：
    1. 级联查询
    2. 本地调用显示不出"xx.xx"形式返回对象的方法
* **修复时间**：2022-08-23
* **下载**：[引擎包 3.9.10_hotfix_0823](https://manateeai.oss-cn-hangzhou.aliyuncs.com/deploy/%E5%BC%95%E6%93%8E%E5%8E%86%E5%8F%B2%E7%89%88%E6%9C%AC/3.9.10_manatee_hotfix_0823.zip)
### 新增
* MySQL 批量查询：支持多个 in 查询
* MySQL 批量查询和 MySQL 单个查询组件增加向下级联查询
* FTP 和 SFTP 组件的上传、下载
* 邮件通知组件
* ClickHouse 增加+ClickHouseSql 组件
* 结构化数据解析函数：xml、csv 等类型字符串的解析
### 修复
* 模糊查询参数为空的时候丢失百分号
* MySQL 更新 in 查询拼接 SQL 出错
* dubbo 调用空指针异常
 
### 下载地址
[引擎包 3.9.10](https://manateeai.oss-cn-hangzhou.aliyuncs.com/deploy/%E5%BC%95%E6%93%8E%E5%8E%86%E5%8F%B2%E7%89%88%E6%9C%AC/3.9.10_manatee.zip)

---

## 3.9.9 版本（2022 年 07 月 28 日）
### 修复
* MySQLsql 分页框输入内容调试后丢失
* long 值转换问题
* log 函数不能取之前的数据，等号引号等特殊符号会打印##DENGYH##等处理后的字符串

### 下载地址
[引擎包 3.9.9](https://manateeai.oss-cn-hangzhou.aliyuncs.com/deploy/%E5%BC%95%E6%93%8E%E5%8E%86%E5%8F%B2%E7%89%88%E6%9C%AC/3.9.9_manatee.zip)

---




## 3.9.8 版本（2022 年 07 月 20 日）

### 3.9.8_hotfix_0803
* **修复**：MySQL 查询组件模糊查询(sql 表达式中使用 like)时候，参数为空时去掉该条件，concat 时若参数为空则为('%%')
* **修复时间**：2022-08-03
* **下载**：[引擎包 3.9.8_hotfix_0803](https://manateeai.oss-cn-hangzhou.aliyuncs.com/deploy/%E5%BC%95%E6%93%8E%E5%8E%86%E5%8F%B2%E7%89%88%E6%9C%AC/3.9.8_manatee_hotfix_0803.zip)

### 3.9.8_manatee_hotfix_0811
* **修复**：当入参和系统变量存在同名变量时，MySQLSql 组件应该去入参的值，却取了系统变量的值。
* **修复时间**：2022-08-011
* **下载**：[3.9.8_manatee_hotfix_0811](https://manateeai.oss-cn-hangzhou.aliyuncs.com/deploy/%E5%BC%95%E6%93%8E%E5%8E%86%E5%8F%B2%E7%89%88%E6%9C%AC/3.9.8_manatee_hotfix_0811.zip)

### 新增

- 支持达梦数据库
- sha、rsa、MD5、国密等常用加解密算法
- 故障排查优化：log 函数、流程调用链路日志
- 本地调用支持枚举类
- rest 组件支持传递 token
### 优化

- lowcode_module 表  'code' ，'name' ， 'description'， 'type' 字段名修改为'module_code' ，'module_name' ， 'module_description'， 'module_type' 
### 修复

- MySQLsql 查询结果为单个少了字段名大小写的配置
- 本地调用组件不能调用基本类型
- MySQLsql 组件查询第二页 totalcount 和 totalpage 失效
- 双层循环时调试结果是正确的，但会因为 debug 报错

### 更新提示
3.9.8 引擎对 lowcode_base_module 表部分字段名了做了修改，从 3.9.7 升级到 3.9.8 需要执行以下 sql 修改字段。
* 老项目：[3.9.7-3.9.8 应用增量脚本.sql](https://www.yuque.com/attachments/yuque/0/2022/sql/12452833/1662023038993-88670387-5629-4acb-a0e5-d0915089f852.sql?_lake_card=%7B%22src%22%3A%22https%3A%2F%2Fwww.yuque.com%2Fattachments%2Fyuque%2F0%2F2022%2Fsql%2F12452833%2F1662023038993-88670387-5629-4acb-a0e5-d0915089f852.sql%22%2C%22name%22%3A%223.9.7-3.9.8%E5%BA%94%E7%94%A8%E5%A2%9E%E9%87%8F%E8%84%9A%E6%9C%AC.sql%22%2C%22size%22%3A145474%2C%22type%22%3A%22%22%2C%22ext%22%3A%22sql%22%2C%22source%22%3A%22%22%2C%22status%22%3A%22done%22%2C%22mode%22%3A%22title%22%2C%22download%22%3Afalse%2C%22taskId%22%3A%22ub9a69ab9-912a-468e-b231-92af8c17348%22%2C%22taskType%22%3A%22transfer%22%2C%22id%22%3A%22u65de02e7%22%2C%22card%22%3A%22file%22%7D)
* 新项目：[3.9.8 应用全量脚本.sql](https://www.yuque.com/attachments/yuque/0/2022/sql/12452833/1662023039005-ab1e7d24-888f-4967-8945-d7b407258077.sql?_lake_card=%7B%22src%22%3A%22https%3A%2F%2Fwww.yuque.com%2Fattachments%2Fyuque%2F0%2F2022%2Fsql%2F12452833%2F1662023039005-ab1e7d24-888f-4967-8945-d7b407258077.sql%22%2C%22name%22%3A%223.9.8%E5%BA%94%E7%94%A8%E5%85%A8%E9%87%8F%E8%84%9A%E6%9C%AC.sql%22%2C%22size%22%3A385067%2C%22type%22%3A%22%22%2C%22ext%22%3A%22sql%22%2C%22source%22%3A%22%22%2C%22status%22%3A%22done%22%2C%22mode%22%3A%22title%22%2C%22download%22%3Afalse%2C%22taskId%22%3A%22u115a9e40-48ab-4407-bbd8-31d4aaad656%22%2C%22taskType%22%3A%22transfer%22%2C%22id%22%3A%22u8b2e97b6%22%2C%22card%22%3A%22file%22%7D)

再次发布时**线上环境**的 lowcode_base_module 表，字段也要修改，线上修改字段名 sql 如下：
```sql
ALTER TABLE `lowcode_base_module`
CHANGE COLUMN `code` `module_code` varchar(45) CHARACTER SET utf8 COLLATE utf8_general_ci NOT NULL COMMENT '英文名称' AFTER `id`,
CHANGE COLUMN `name` `module_name` varchar(32) CHARACTER SET utf8 COLLATE utf8_general_ci NOT NULL COMMENT 'api 名称' AFTER `module_code`,
CHANGE COLUMN `description` `module_description` varchar(256) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL COMMENT '接口描述' AFTER `module_name`,
CHANGE COLUMN `version` `module_version` varchar(16) CHARACTER SET utf8 COLLATE utf8_general_ci NOT NULL DEFAULT 'v1.0.0' COMMENT '版本' AFTER `module_description`,
CHANGE COLUMN `type` `module_type` tinyint(4) NOT NULL DEFAULT 1 COMMENT '接口模块 1   计算模块 2  子模块  0' AFTER `project_id`,
MODIFY COLUMN `id` bigint(20) UNSIGNED NOT NULL AUTO_INCREMENT FIRST,
MODIFY COLUMN `package_id` bigint(20) NOT NULL DEFAULT 0 COMMENT '包 id' AFTER `env`,
MODIFY COLUMN `project_id` bigint(20) NOT NULL DEFAULT 0 COMMENT '项目 id\\n0 代表系统' AFTER `package_id`,
MODIFY COLUMN `request_mode` varchar(16) CHARACTER SET utf8 COLLATE utf8_general_ci NOT NULL DEFAULT 'POST' COMMENT '请求方式：GET/POST' AFTER `module_type`,
MODIFY COLUMN `is_login` tinyint(4) NOT NULL DEFAULT 0 COMMENT '是否需要登录，需要  0  不需要 1' AFTER `request_mode`,
MODIFY COLUMN `gmt_create` datetime NOT NULL DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间' AFTER `valid`,
MODIFY COLUMN `gmt_modified` datetime NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP COMMENT '修改时间' AFTER `gmt_create`,
MODIFY COLUMN `create_user` bigint(20) NOT NULL DEFAULT 0 COMMENT '创建用户 id' AFTER `interrupt`,
MODIFY COLUMN `modified_user` bigint(20) NOT NULL DEFAULT 0 COMMENT '更新用户 id' AFTER `create_user`,
ADD `sort` int(11) DEFAULT '1' COMMENT '排序' AFTER `conf`;
```

### 下载地址
[引擎包 3.9.8](https://manateeai.oss-cn-hangzhou.aliyuncs.com/deploy/%E5%BC%95%E6%93%8E%E5%8E%86%E5%8F%B2%E7%89%88%E6%9C%AC/3.9.8_manatee.zip)