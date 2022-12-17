---
sidebar_position: 10
---
# 预发与线上环境隔离

### 配置项目的配置文件
预发环境配置文件：
```yaml
manatee:
  moudelEnv: pre
```
线上环境配置文件：
```yaml
manatee:
  moudelEnv: prod
```
### 操作步骤
1. 从日常/开发环境导出 lowcode_base_module 表里的接口数据

2. 导入到预发/线上数据库，发布预发环境(注意确保 env 字段的值为"pre"，后续会通过产品功能导出对应环境的 SQL，目前需要手动)

3. 发布线上环境，sql 如下（注意替换 delete 语句中的 project_id 值）
```sql
delete from lowcode_base_module where env = 'prod' and project_id = xxx;

insert into lowcode_base_module (module_code, module_name, module_description, module_version, env, package_id, project_id, module_type, request_mode, is_login, process_conf, valid, gmt_create, gmt_modified, params, mock, chart_url, interrupt, create_user, modified_user, system_version, conf, sort) select module_code, module_name, module_description, module_version, 'prod' as env, package_id, project_id, module_type, request_mode, is_login, process_conf, valid, gmt_create, gmt_modified, params, mock, chart_url, interrupt, create_user, modified_user, system_version, conf, sort from lowcode_base_module where env = 'pre';
```
