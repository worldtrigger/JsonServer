# JSONServer 使用 MockJs 以及 MockJs 语法

## JSONServer 使用 MockJs

### (1)安装包依赖

- 前提已经按照上一步安装了 jsonServer

```javascript
cnpm install mockjs -D
```

### (2)mockjs 配合 JsonServer 使用

- 把 db.json 换成 app.js 然后 app.js 里面写

```javascript
const Mock = require('mockjs');
module.exports = () => {
  var data = Mock.mock({
    'course|20': [
      {
        'id|+1': 1000,
        name: '@ctitle(5,10)',
        author: '@cname',
        college: '@ctitle(6)',
        'category_Id|1-6': 1,
      },
    ],
    'course_category|6': [
      {
        'id|+1': 1,
        pid: -1,
        cName: '@ctitle(4)',
      },
    ],
  });
  return data;
};
```

### (3)运行的时候

```javascript
json-server --watch app.js
```

## Mock 数据规则

### 字符串

- 'name|min-max':string

> 通过重复 string 生成一个字符串,

```javascript
Mock.mock({
  'string|1-10': '★',
});
```

- 结果

```bash
//随机几个星
{
  "string": "★★★★★★★"
}
```

### 数字

- 'name|+1': number

> 自增

```javascript
Mock.mock({
  'number|+1': 202,
});
```

- 'name|min-max.dmin-dmax': number

```javascript
Mock.mock({
  'number|1-100.1-10': 1,
});
```

> 结果

```javascript
{
  "number": 48.03617355
}
```

### Boolean

```javascript
'name|1': boolean
```

- 结果

```javascript
{
  "boolean": true
}
```

### Object

- 'name|count': object

```javascript
Mock.mock({
  'object|2': {
    310000: '上海市',
    320000: '江苏省',
    330000: '浙江省',
    340000: '安徽省',
  },
});
```

> 结果

```bash
{
  "object": {
    "320000": "江苏省",
    "330000": "浙江省"
  }
}
```

### Array

- 代码

```javascript
Mock.mock({
  'array|1-10': [
    {
      'name|+1': ['Hello', 'Mock.js', '!'],
    },
  ],
});
```

- 结果

```bash
{
  "array": [
    {
      "name": "Hello"
    },
    {
      "name": "Mock.js"
    },
    {
      "name": "!"
    },
    {
      "name": "Hello"
    },
    {
      "name": "Mock.js"
    },
    {
      "name": "!"
    },
    {
      "name": "Hello"
    }
  ]
}
```

- 第二种不是对象

```javascript
Mock.mock({
  'array|3': ['Hello', 'Mock.js', '!'],
});
```

- 结果

```bash
{
  "array": [
    "Hello",
    "Mock.js",
    "!",
    "Hello",
    "Mock.js",
    "!",
    "Hello",
    "Mock.js",
    "!"
  ]
}
```

### 随机方法

- 随机 5-10 个中文字 name,title

```javascript
Mock.mock({
  course_name: '@ctitle(5,10)',
  autor: '@cname',
  college: '@ctitle(6)',
});
```
