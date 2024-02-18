# MongoDB常见用法


## 修改数据

 
```
update方法：该方法已被弃用，建议使用新的方法 updateOne()、updateMany() 或者 bulkWrite() 来代替。
db.yourCollectionName.update({}, {$unset: {字段名: ""}},{multi: true});
```

```
updateMany() 是 MongoDB 中的一个方法，用于在集合中更新满足指定条件的多个文档。它的作用类似于 SQL 中的 UPDATE 语句，但可以同时更新多个文档。

以下是 updateMany() 方法的一般语法：
db.collection.updateMany(
   <filter>,   // 过滤条件，确定要更新哪些文档
   <update>,   // 更新操作，指定要对匹配的文档执行的更新操作
   <options>   // 可选参数，用于控制更新行为的其他选项
)
<filter>：这是一个 JSON 对象，用于指定更新操作应该应用于哪些文档。只有满足这个过滤条件的文档才会被更新。
<update>：这也是一个 JSON 对象，用于指定要对满足过滤条件的文档执行的更新操作。常用的更新操作符包括 $set（设置字段的值）、$unset（移除字段）、$inc（增加或减少数值字段的值）等。
<options>：这是一个可选参数，用于控制更新行为的其他选项。常见的选项包括 upsert（如果匹配的文档不存在，则插入新文档）、arrayFilters（用于更新数组字段中的特定元素）等。
// 更新集合中所有年龄大于 30 的文档，将其年龄减少 10
db.users.updateMany({ age: { $gt: 30 } }, { $inc: { age: -10 } })

db.yourCollectionName.updateMany({}, {$unset: {字段名: ""}},{multi: true});
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