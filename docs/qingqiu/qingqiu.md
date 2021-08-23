# 数据请求和渲染

## (1) 地址

### 属性的开头就表示地址

- 如下:地址就有三个,对应的就是 posts,comments,profile

- http://localhost:4000/posts

- http://localhost:4000/comments

- http://localhost:4000/profile

```json
{
  "posts": [{ "id": 1, "title": "json-server", "author": "typicode" }],
  "comments": [{ "id": 1, "body": "some comment", "postId": 1 }],
  "profile": { "name": "typicode" }
}
```

## (2) 请求

- GET,POST,PUT,PATCH,DELETE 等请求的 API,分别对应数据的所有类型的实体

```bash

# 获取所有数据, xxx就是属性名(地址)

GET /xxx


# 获取xxxx下id为2的所有信息

GET /xxx/2


# 添加信息请求body中必须包含xxx里面的属性数据,json-server自动保存

POST /xxx

# 修改课程,请求中必须包含修改的数据,只能通过id来修改

PUT /xxx/1

PATCH  /XXX/1

# 删除课程信息,只能通过id来删除

DELETE /xxx/1

```

> 总结如下 获取都是 GET,添加都是 POST,修改都是 PUT,删除都是 DELETE

## 获取的时候过滤数据

### 属性联合

- 可以用.访问更深层的属性

```bash
GET /posts?title=json-server&author=typicode
GET /posts?id=1&id=2

# 可以用 . 访问更深层的属性。
GET /comments?author.name=typicode
```

### 四则运算

- \_gte 大于等于

- \_lte 小于等于

- \_ne 不等于

- \_like 包含

```bash
GET /posts?id_ne=1
GET /posts?id_lte=100
GET /posts?title_like=server
```

### 排序

- 参数\_sort 设定排序的字段

- 参数 \_order 设定排序的方式(默认升序)

```bash
GET /posts?_sort=views&_order=asc(升序)
GET /posts/1/comments?_sort=votes&_order=desc (降序)
```

- 也支持多字段排序

```bash
GET /posts?_sort=user,views&_order=desc,asc
```

### 切片数据

- \_start&\_end

```bash
GET /posts?_start=20&_end=30
GET /posts/1/comments?_start=20&_end=30
GET /posts/1/comments?_start=20&_limit=10
```

### 获取全文检索

- q=xxx

```bash
GET /posts?q=第三条
```
