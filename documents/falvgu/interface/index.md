## 法律谷接口

### 找律师

1. 根据案情描述判断案由`case_type`

请求字段：
```javascript
req = {
    text: '借款'
}
```

返回字段：
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

请求字段：
```javascript
req = {
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

返回字段：
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

### 找案例

1. 根据案情描述查找相似案例

请求字段：
```javascript
req = {
    text: '某某借我钱不还',
    filter: {
        court_id: '',
        year: '',
        level: '',
        court_level: '',
        doctype: ''
    },
    keyWord: '',    //关键词
    orderBy: '',
    pageNum: 0
}
```

返回字段：
```javascript
res = {
    oageCount: 50,
    recordCnt: 1000,
    t: 0.26903414726257,
    dataList: [
        {
            _id: '5db5f14fdd4bf0c687158b52b924b7c8',
            caseDate: '2014-02-06',
            caseId: '(2013)五民一初字第02055号',
            caseType: '民间借贷纠纷',
            court: '安徽省五河县人民法院',
            r: 1.03086,
            reasonList:["本院认为，原告主张被告货款14000万元，事实清楚，证据充分，本院予以认定。依照《中华人民共和国民法通则》第八十四条、第一百零八条及《中华人民共和国民事诉讼法》第一百四十四条的规定，"],
            resultList: [
                "判决如下：",
                "被告左宗义欠原告李伟英款14000元于本判决书生效后10日内付清。",
                "如果未按本判决指定的期间履行给付金钱的义务，应当依照《中华人民共和国民事诉讼法》第二百二十九条之规定，加倍支付迟延履行期间的债务利息。",
                "案件受理费150元，由被告承担。",
                "如不服本判决，可在判决书送达之日起15内，向本院递交上诉状，并按对方当事人的人数提出副本，上诉于蚌埠市中级人民法院。"
            ],
            title: '李伟英诉左宗义民间借贷纠纷初审判决书'
        },
        ...//共返回20个案例
    ]
}
```