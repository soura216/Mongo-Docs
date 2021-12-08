```
{ "_id" : ObjectId("61ab5c18e81bb48b8dd98290"), "name" : "Soura", "age" : 27, "salary" : 700000, "skills" : [ "JS", "Angular", "Node JS" ], "address" : { "city" : "Kolkata", "state" : "West Bengal" }, "awards" : [ { "name" : "INSTA", "year" : 2021 }, { "name" : "RISE", "year" : 2021 }, { "name" : "INSTA1", "year" : 2020 } ] },
{ "_id" : ObjectId("61ab5c18e81bb48b8dd98291"), "name" : "Soumya", "age" : 28, "salary" : 800000, "skills" : [ "Android", "Java", "Git" ], "address" : { "city" : "Bhuvneshwar", "state" : "Odisha" }, "awards" : [ { "name" : "Global", "year" : 2021 }, { "name" : "RISE", "year" : 2021 }, { "name" : "INSTA", "year" : 2020 } ] },
{ "_id" : ObjectId("61ab5c18e81bb48b8dd98292"), "name" : "Subhra", "age" : 27, "salary" : 100000, "skills" : [ "CSS", "Angular", "Git" ], "address" : { "city" : "Kolkata", "state" : "West Bengal" }, "awards" : [ { "name" : "RISE1", "year" : 2021 }, { "name" : "INSTA", "year" : 2020 } ] }
```
<hr/>

**Read**

- Array with Object
```
db.employee.find({'name':'Subhra','awards':{$elemMatch:{'name':{$in:['INSTA','RISE']}}}}) 

db.employee.find({'name':'Subhra','awards.name':{$all:['INSTA','RISE1']}}) 
```

- Array
```
db.employee.find({'name':'Subhra','skills':{$elemMatch:{$in:['Git']}}})

db.employee.find({'name':'Subhra','skills':{$eq:'Git'}})
```

- Object
```
db.employee.find({'address.city':'Kolkata'})
```
<hr/>

**Distinct**

- Array With Object
```
db.employee.distinct('awards.name')
```

- Array
```
db.employee.distinct('skills')
```

- Object
```
db.employee.distinct('address.city')
```

<hr/>

**Update ~ $pull**

- Array with Object
```
db.employee.updateMany(
    {'name':'Soumya'},
    {$pull:{'awards':{'name':'INSTA'}}}
)
```
- Array
```
db.employee.updateMany(
    {'name':'Soumya'},
    {$pull:{skills:{$in:["Java","Git"]}}}
)
```

<hr/>

**Update ~ $pullAll**
```
db.employee.updateMany(
    {'name':'Subhra'},
    {$pullAll:{skills:["Angular","Gits"]}}
)
```
<hr/>

**Update ~ $push**
- Array with Object
```
db.employee.updateMany(
    {'name':'Subhra'},
    {$push:{awards:{$each:[{ "name" : "INSTA2", "year" : 2021 },{ "name" : "RISE1", "year" : 2021 }],$position:0}}}
)
```

- Array
```
db.employee.updateMany(
    {'name':'Subhra'},
    {$push:{skills:{$each:["Angular","HTML"],$position:0}}}
)
db.employee.updateMany(
    {'name':'Subhra'},
    {$push:{skills:'Phython'}}
)
```

<hr/>









