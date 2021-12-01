# Update

- One document
    ```
    db.products.update(
        {manufacturer: "apple"},
        {$set:{"year_of_launch":2018}}
    )

    ```
    * If property doesn't exist then it would create new field with value
    ```
    db.products.updateOne(
        {"prodname" : "iphone 7"},
        {$set:{"year_of_launch":2019}}
    )
    ```


- Multiple document
```
db.products.updateMany(
    {manufacturer: "apple"},
    {$set:{"year_of_launch":2021}}
)

```

- Unset ($unset ~ operator) 

    * If property exist
        ```
        db.products.updateOne(
            {manufacturer: "apple"},
            {$unset:{"year_of_launch":2019}}
        )
        ```

    * If property doesn't exist
        ```
        db.products.updateOne(
            {"prodname" : "iphone 7"},
            {$unset:{"year_of_launch":2019}}
        )

        Note: It doesn't give any error If property doesn't exist
        ```

- Increment ($inc  ~ operator) 
    ```
    Note: 
    ~ If property doesn't exist then it would create new field with value
    ~ If property exists but the value of property is not numeric then it will get error

    db.products.updateOne(
        {"_id" : ObjectId("61a3bf0eb6db30c378b51f60")},
        {$inc:{"price":+1000}}
    )

    db.products.updateOne(
        {"_id" : ObjectId("61a3bf0eb6db30c378b51f60")},
        {$inc:{"rating":-2}}
    )
    ```

- Push ($push ~ operator)    
    ```
    Note: 
    ~ If property doesn't exist then it would create new field with value   
    ~ If property exists but the value of property is not an array then it will get error

    db.products.updateOne(
        {"_id" : ObjectId("61a3bf0eb6db30c378b51f62")},
        {$push:{"colors":"red"}}
    ) 
    
    ```
    * If u want to push multiple value ($each, $position, $slice  ~ operators )
    ```
        db.products.updateOne(
            {_id:ObjectId("61a3bf0eb6db30c378b51f62")},
            {$push:{colors:{$each:["black","white"],$position:2,$slice:4}}}
        )
    ```  
-  $addToSet operator

    >_Note: If the passing value doesn't exist inside the array then only it can work_
    ```
    db.blog.update({"blogid":1},{$addToSet:{"comments":"bed"}})
    ```

- Upsert & $setOnInsert operator   
    ```
    Note:
    ~ Should where condition fail i.e this particular document doesn't exist
    ~ {upsert:true} flag should be mentioned
    ~ One document will insert and as properties of document would be "where conditional property" + "set property" + "setOnInsert property"  

    db.products.updateOne(
       {"_id" : 21344555},
       {$set:{"prodname" : "mi m31", "manufacturer" : "mi"},$setOnInsert:{"price":70000}}, 
       {"upsert":true} 
    )  
    ```

- maximum ($max ~ operator)    
    ```
    Note: 
    ~ If property doesn't exist then it would create new field with value
    ~ If property exists but the value of property is not numeric then it will get error
    ~ If passing value greater than existing value then only value would update

    db.products.updateOne(
        {"_id" : 21344555},
        {$max:{"price":80001}}
    )
    ```

- maximum ($min ~ operator)    
    ```
    Note: 
    ~ If property doesn't exist then it would create new field with value
    ~ If property exists but the value of property is not numeric then it will get error
    ~ If passing value less than existing value then only value would update

    db.products.updateOne(
        {"_id" : 21344555},
        {$min:{"price":80003}}
    )
    ```       

- $pull update operator:

    >_It works if the element is either array or array with Object._
    >_It works even if you use any condition operator in query syntax._

    ```
        db.blog.update({"blogid":1},{$pullAll:{"comments":{"name":"Phil","comment":{$eq:"Test"}}}})
    ```

- $pullAll update operator:

    >_It only works if the element is array._
    >_It only works if you don't use any condition operator in query syntax_    

    ```
        db.users.update( {"name":{$eq:"Soura"}}, {$pullAll:{"skills":["JS","Angular"]}})
    ```

- $rename operator:
    ```
        db.blog.update( {"blogid" : 1}, {$rename:{"title":"titles"}})
    ```    



