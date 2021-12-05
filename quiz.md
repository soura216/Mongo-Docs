We need to get the teamMate(empid’s)  and for those empid’s in the teammate array, we need to aggregate the SMEin and their count
```
{ "_id" : ObjectId("61aced5030abbb44e718438d"), "empid" : 1011, "empname" : "Rakesh", "SMEin" : [ "Angular", "Node", "MongoDB" ], "teamMates" : [ 1012, 1045, 1056 ] }
{ "_id" : ObjectId("61aced5030abbb44e718438e"), "empid" : 1012, "empname" : "Vivek", "SMEin" : [ "Vuejs", "Node", "MongoDB" ], "teamMates" : [ 1011, 1045, 1056 ] }
{ "_id" : ObjectId("61aced5030abbb44e718438f"), "empid" : 1045, "empname" : "Ben", "SMEin" : [ "Polymer", "Node", "MongoDB" ], "teamMates" : [ 1012, 1011, 1056 ] }
{ "_id" : ObjectId("61aced5030abbb44e7184390"), "empid" : 1056, "empname" : "Lavanya", "SMEin" : [ "Angular", "Node", "MongoDB" ], "teamMates" : [ 1012, 1045, 1011 ] }

db.employees.aggregate([
    {$match:{empid:1011}},
    {$unwind: '$teamMates'},
    {$lookup:{from:'employees',localField:'teamMates',foreignField:'empid',as:'teamMatesInfo'}},
    {$project:{teamMatesInfo:{$arrayElemAt:['$teamMatesInfo',0]}}},
    {$unwind:'$teamMatesInfo.SMEin'},
    {$group:{_id:'$teamMatesInfo.SMEin',count:{$sum:1}}}
]).pretty()
```

>_localField will be either own field or array field_
>_You have to do $unwind before write the query for group and one-many relation_