# Delete

- One document
```
db.product_catalog.deleteOne( { prodname: "Java for Dummies"} )
```

- Multiple document
```
db.employee.deleteMany( { name: {$in: ["Soura Ghosh","Soumya Ghosh"] }} )
```