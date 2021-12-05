* Count
```
db.employee.find({name:{$exists:true}}).count()
```

* Distinct

```
db.employee.distinct('age',{salary:{$gte:100000}})

db.employee.distinct('address.city',{'address.city':{$in:["Kolkata","Mumbai"]}})

db.employee.distinct('awards.0.name',{'awards':{$elemMatch:{year:{$in:[2021,2020]}}}})

db.employee.distinct('skills')
```