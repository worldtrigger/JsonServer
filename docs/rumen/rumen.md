# Json-server 入门介绍

## Json-server 是什么

能够快速的给前端开发人员提供后端接口的服务工具

## Json-server 使用场景

在开发阶段 后端人员无法提供接口,前端为了减少等待事件，需要模拟接口,进行数据的增删改查

## Json-server 的安装

### 全局安装

```javascript
cnpm install json-server -g
```

### 新建目录,在目录中新建一个 db.json 文件,里面写入假数据

- 特别强盗要是数组 默认数据里面必须有 id 选项,但是发射数据的时候可以不带 id,他会自动填写

```javascript
{
  "posts": [
    { "id": 1, "title": "json-server", "author": "typicode" }
  ],
  "comments": [
    { "id": 1, "body": "some comment", "postId": 1 }
  ],
  "profile": { "name": "typicode" }
}
```

### 启动 json-server

```javascript
json-server db.json
```

### 配置 json-server

- 在根目录创建 json-server.json 文件, 然后写下以下代码,然后执行 json-server db.json

- static 挂载静态文件的

```javascript
{
  "port":4000,
  "watch":true,
  "static":"./"
}
```
