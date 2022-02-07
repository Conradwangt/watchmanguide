# 1. DataMo suggested resources：
| App                     | Config  | Number of instances:product   | Cluster         |Optional|
| ------------------------ | ----- | ------- | ------------- |------|
| watchmen-matryoshka-doll | 4C8G  | 8 | 2 nodes         |required|
| watchmen-web-client      | 2C2G  | 1 | 2 nodes         |required|
| watchmen-matryoshka-dqc  | 2C8G  | 1 | 1 node，single app |required|
| presto                   | 4C16G | 1 | 3 nodes        |required|
| collector                | ----  | ------ | ------        |optional|
# 2. Version requirements:

* Mysql >= **5.8.0**
* Oracle >= **12.2.0.1.0**
* Chrome >= **85.0** or Edge >= **92.0**

# 3. Build process

1. 发布docker-all.repo.ebaotech.com/dataplatform/dataplatform-datamo-dbscript:1.0.3（定义库）

` 
定义库只有在第一次发布的时候初始化数据库，建一些系统表。比如topic表和piepline表.
`

template https://oss.ebaotech.com/datamo/datamo-material/datamo-db-deployment

2. 发布watchmen组件（web client ， doll， dqc， presto）

`
争对开发环境需要进行topic和pipeline的配置，因此必须只配置一个doll.
`

3. 创建zone，user， datasource（在线操作，项目组完成）

`
只有在第一次发布时在前端页面创建租户、使用账户、datasource(实例库地址)
`

参考 https://oss.ebaotech.com/datamo/datamo-material/datamo-user-guide/-/tree/master/watchman-superuser-user-guide

4. 发布docker-all.repo.ebaotech.com/dataplatform/seacloud-db-deploy:{version} （实例库)， version由项目组确认

`
实例库指的是topic对应的表的所在的库，也就是在前端页面建的那些表，这里只是表。如果发生需求变更，比如表新加一个字段，那么需要在实例库中对该表新加字段，发布的时候至少需要同时发布db-deploy和config-deploy
`

template https://oss.ebaotech.com/datamo/datamo-material/datamo-config-deployment


5. 发布docker-all.repo.ebaotech.com/dataplatform/seacloud-config-deploy:{version} ，version由项目组确认

`
config 是指配置的topics和pipelines定义，存在的形式为markdown，它们可以直接从pipeline group界面导出，导入。如果导入后就存到topic和pipelines表中了。这些定义主要描述了topic的字段，流转形式。举个例子，如果发生需求变更，某个字段A的值需要在其他字段为B的情况下为C，那么 db中表以及字段都没有发生变化，只有topic和pipelines表中的记录内容发生变更，此时
config-deploy发生更新，一般情况下需要同时发布db-deploy和config-deploy.
`

6. 在线检查所有topic的datasource，进行topic的datasource设置

`
使用第三步建立的账户登录前端页面操作。只有在添加新的topic的时候需要.
`

参考 https://oss.ebaotech.com/datamo/datamo-material/datamo-user-guide/-/tree/master/watchman-superuser-user-guide

7. 修改presto配置，支持新的datasource配置

`
只有在第一次发布时在presto 机器上配置，添加properties.
`

参考 https://oss.ebaotech.com/datamo/datamo-material/datamo-user-guide/-/tree/master/watchman-superuser-user-guide









