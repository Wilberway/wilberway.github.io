##法律谷接口

###找律师

1. 根据案情描述判断案由`case_type`

请求字段
```javascript
q = {
    text: '借款'
}
```
返回字段
```javascript
res = [
    ["借款合同纠纷",["关键词1","关键词2","关键词3"],4012400],
    ["保证合同纠纷",["关键词1","关键词2","关键词3"],4012500],
    ["合同纠纷",["关键词1","关键词2","关键词3"],4010000],
    ["不当得利纠纷",["关键词1","关键词2","关键词3"],4020000],
    ["与公司相关的纠纷",["关键词1","关键词2","关键词3"],8020000],
]
```

2. 根据案由和地区请求律师信息

请求字段
```javascript
q = {
    text: '借款',
    keyWord: '',
    orderBy: '',
    amounts: '',
    casetypename: '借款合同纠纷',
    filter: {
        casetype: [4012400],
        court_id: 20020000
    },
    pageNum: 0
}
```

返回字段
```javascript
res = {
    dataList: [
        {
            amountMax: 341,
            certification: 0,
            goodAtFieldList:[
                {
                    caseNum: 10,
                    caseTypeName: "借款合同纠纷"
                },
                {
                    caseNum: 1,
                    caseTypeName: "银行卡纠纷"
                },
                {
                    caseNum: 1,
                    caseTypeName: "与公司有关的纠纷"
                }
            ],
            id: "wV77u0dmCKRETanTZeWBZA==",
            lawyerInc: "广东中深律师事务所",
            lawyerName: "谭洪武",
            mainWorkLoc: "深圳",
            photoUrl: "http://falvgu-img.b0.upaiyun.com/lawyer/0f016e157e3ebd998eede6e213fb5a41",
            similarCase: {
                caseControversy: ["债务的清偿", "债的定义与债的履行", "借款的返还", "逾期利息", "自然人之间的借款合同利率", "预扣借款利息行为的禁止"],

                
                caseName: "冯光壬与杨坤芳,杨新梅民间借贷纠纷二审民事判决书",
                id: "7cd88ae1387138c3e7d553e55621ed27",
                judgementDate: "2015-05-05",
                score: 0.76738
            },
            workAge: 0
        }
    ],
    pageCount: 34,
    recordCnt: 1000
}
```