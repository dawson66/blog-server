---
title: MongoDB入门
tags: Node
categories:
  - Node
cover: mongo.jpeg
abbrlink: '661780e7'
date: 2021-05-05 20:03:30
---

### mongoDB 

#### 安装

1. **Mac:**官网下载taz压缩包直接解压到指定目录 `/Users/wangmeng/Documents/database/mongodb/`
2. **Windows:**

#### 启动

1. **Mac：**运行mongodb 需进入安装目录的`/bin`目录且指定数据库存放地址 ，`./mongod --dbpath /Users/wangmeng/Documents/database/db`
2. **Windows：**会选择在输入命令`mongod`所属盘符根目录下 `/data/db`作为自己的数据存储目录，所以在第一次执行该命令之前先自己手动在根目录下新建一个`/data/db`目录。如果想要修改默认的数据存储目录，可以：`mongod --dbpath=数据存储目录路径`

#### GUI

mongodb GUI界面：Robo 3T 下载地址：[Robo 3T](www.robomongo.org)

#### 连接

`mongo`：该命令默认连接本机的MongoDB服务。

**Mac**：连接mongodb同样需要在安装目录的`bin`目录下，执行`./mongo`即可成功。

**Windows**：直接`mongo`即可。

#### 退出

`exit`：在连接状态输入即退出连接。

#### 基本命令

* `show dbs`：查看所有数据库（涵盖系统数据库admin,local及用户含数据的数据库，若无数据则不会显示）

* `db`：查看当时操作的数据库

* 创建数据库

  * `use database_name`：切换到指定的数据库（如果没有则会新建）

* 删除数据库

  * `db.dropDatabase()`

* 创建集合

  * `db.createCollection(name,options)`

* 插入文档（之所以叫文档，是因为数据组织形式为JSON）

  * `db.COLLECTION_NAME.insert(document)`

  * `db.COLLECTIONS_NAME.insertOne(document)`
  * `db.COLLECTIONS_NAME.insertMany()`

* 更新文档

  * `db.collection.update()`
  * `db.collection.save()`

* 删除文档

* 