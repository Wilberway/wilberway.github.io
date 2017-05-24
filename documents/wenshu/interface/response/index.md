# 分析工具返回接口定义

### 1. 案由维度返回数据

* 胜诉率、败诉率、部分胜诉率

返回一个三个数字组成的数组，分别代表胜诉率、败诉率、部分胜诉率，每项0~100代表0%~100%。

格式如下：

```javascript
//胜诉率30%，败诉率45.5%，部分胜诉率24.5%
totalRatio = [30,45.5,24.5]
```

- 律师案件数排名

  返回律师的数据，需要按案件数量排名，也以数组格式返回。

  格式如下：

  ```javascript
  //name:律师姓名，num:案件数量，id:律师id，其中id为律师的唯一标示符
  caseRank = [
    {
      name: "张三",
      num: 999,  
      id: 5632
    },
    {
      name: "李四",
      num: 456,  
      id: 1232
    },
    {
      name: "王五",
      num: 123,  
      id: 8446
    }
  ]
  ```

- 律师胜诉率排名，律师部分胜诉率排名

  数据格式同上，也以数组格式返回。

  格式如下：

  ```javascript
  //name:律师姓名，ratio:胜诉率，id:律师id，其中id为律师的唯一标示符
  allWinRatio = [
    {
      name: "张三",
      ratio: 80,  
      id: 5632
    },
    {
      name: "李四",
      ratio: 75.5,  
      id: 1232
    },
    {
      name: "王五",
      ration: 60,  
      id: 8446
    }
  ]

  //name:律师姓名，ratio:部分胜诉率，id:律师id，其中id为律师的唯一标示符
  partWinRatio = [
    {
      name: "张三",
      ratio: 20,  
      id: 5632
    },
    {
      name: "李四",
      ratio: 18.8,  
      id: 1232
    },
    {
      name: "王五",
      ration: 16,  
      id: 8446
    }
  ]
  ```


- 返回数据格式示例：

  ```javascript
  responseData = {
    result:1, //标记返回成功，-1则为没有查询到数据，0失败或其他原因
    caseRank: [
      {
        name: "张三",
        num: 999,  
        id: 5632
      },
      {
        name: "李四",
        num: 456,  
        id: 1232
      },
      {
        name: "王五",
        num: 123,  
        id: 8446
      }
    ],
    allWinRatio = [
      {
        name: "张三",
        ratio: 80,  
        id: 5632
      },
      {
        name: "李四",
        ratio: 75.5,  
        id: 1232
      },
      {
        name: "王五",
        ration: 60,  
        id: 8446
      }
    ],
    partWinRatio: [
      {
        name: "张三",
        ratio: 20,  
        id: 5632
      },
      {
        name: "李四",
        ratio: 18.8,  
        id: 1232
      },
      {
        name: "王五",
        ration: 16,  
        id: 8446
      }
    ]
  }
  ```

### 2.律师列表

当查询到有律师时，需要返回律师列表，这是为了解决查询到多个结果的问题（比如重名律师的情况）。

同样地，返回数据为一个数组，格式如下：

```javascript
lawyerList = [
  
]
```







​