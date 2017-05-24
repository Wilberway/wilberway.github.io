# 分析工具请求接口定义

### 1. 案由维度

有两个字段组成：案由和法院

* 案由：

  由一级案由、二级案由等等组成，格式如下：

  ```javascript
  //只查询一级案由
  reason: {
    reason_1: "知识产权与竞争纠纷",
    reason_2: "",
    reason_3: "",
    reason_4: ""
  }
  //查询二级案由
  reason: {
    reason_1: "知识产权与竞争纠纷",
    reason_2: "不正当竞争纠纷",
    reason_3: "",
    reason_4: ""
  }
  ```

  说明：如果只查询一级案由，则只有`reason_1`字段有内容，其他字段为空，以此类推。


- 法院：

  法院由省、市和名称三种格式确定范围，格式如下：

```javascript
//只查询省：
court:{
  province: "广东省",
  city: "",
  name: ""
}
//查询省市：
court:{
  province: "广东省",
  city: "深圳市",
  name: ""
}
//查询名称：
court:{
  province: "",
  city: "",
  name: "广东省深圳市中级法院"
}
```

- 请求数据格式示例：

```javascript
requestData = {
  cmd:"reasonSearch",
  reason: {
    reason_1: "知识产权与竞争纠纷",
    reason_2: "不正当竞争纠纷",
    reason_3: "",
    reason_4: ""
  },
  court:{
    province: "广东省",
    city: "深圳市",
    name: ""
  }
}
```

### 2.律师维度

有两个字段组成：案由和律师

- 案由

  案由的请求数据与上面的案由维度一致，参考案由维度。

- 律师

  查询律师姓名，格式如下：

  ```javascript
  lawyer: "张三"
  ```


- 请求数据格式示例：

  ```javascript
  requestData = {
    cmd:"lawyerSearch",
    reason: {
      reason_1: "知识产权与竞争纠纷",
      reason_2: "不正当竞争纠纷",
      reason_3: "",
      reason_4: ""
    },
    lawyer: "张三"
  }
  ```

  ​