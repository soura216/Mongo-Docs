# Aggregate

- $match ~ operator
>_Note: it works like "where" condition_
```
db.employee.aggregate([
    {$match:{age:{$gte:28}}}
])
```

- $unwind ~ operator
>_Note: it helps to break the array and create the new rows by those array element in output_
```
db.employee.aggregate([
    {$match:{age:{$gte:28}}},
    {$unwind:'$awards'}
])
```

- $project ~ operator
>_Note: it helps to select particular fields which u want to show in output.
Simultaneously u can rename the fields and define the dataType of fields in output_

```
db.employee.aggregate([
    {$match:{age:{$gte:28}}},
    {$unwind:'$awards'},
    {$project:{_id:0,award_name:'$awards.name',award_name_type:{$type:'$awards.name'}}}
])
```

- $group ~ operator
```
db.employee.aggregate([
    {$match:{age:{$gte:27}}},
    {$unwind:'$awards'},
    {$project:{_id:0,award_name:'$awards.name',award_name_type:{$type:'$awards.name'},award_year:'$awards.year'}},
    {$group:{_id:'$award_name',sum_of_year:{$sum:'$award_year'}}}
])
```

- $limit, $skip, $sort ~ operator
```
db.employee.aggregate([
    {$match:{age:{$gte:27}}},
    {$unwind:'$awards'},
    {$project:{_id:0,award_name:'$awards.name',award_name_type:{$type:'$awards.name'},award_year:'$awards.year'}},
    {$group:{_id:'$award_name',sum_of_year:{$sum:'$award_year'}}},
    {$limit:3},
    {$skip:1},
    {$sort:{_id:1}}
])
```

- $out ~ operator
>_Note:You can insert / update the grouping records by $out operator_
```
db.employee.aggregate([
    {$match:{age:{$gte:27}}},
    {$unwind:'$awards'},
    {$project:{_id:0,award_name:'$awards.name',award_name_type:{$type:'$awards.name'},award_year:'$awards.year'}},
    {$group:{_id:'$award_name',sum_of_year:{$sum:'$award_year'}}},
    {$out:'list_of_awards'}
])    
```

- $lookup
```
db.customer.aggregate([
    {$lookup:{from:'resident',localField:'cname',foreignField:'rname',as:'resident_details'}}
]).pretty()
```
