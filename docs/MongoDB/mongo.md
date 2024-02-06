# MongoDB常见用法


## 修改数据

 
```
db.yourCollectionName.update({}, {$unset: {字段名: ""}},{multi: true});
```



## 查询数据


如果某个字段是Long类型，而不是字符串或其他类型，那么使用正则表达式的方式可能会有一些问题。在这种情况下，你可以使用 MongoDB 的 $gte（大于等于）和 $lt（小于）运算符来查询以xxx开头的字段。
```
db.yourCollectionName.find({
  "字段名": {
    $gte: 400000000,   // 大于等于 4 开头的最小值
    $lt: 500000000     // 小于 5 开头的最大值
  }
})
```