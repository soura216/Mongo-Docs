# Read

    db.products.find()

    * Only select fields will display from documents 
      db.products.find({},{_id:0,prodname:1,price:1})

    Note: 1 means appear, 0 means disappear, not mentioned means disappear  

    * Read one document
        db.products.findOne()

    * If u want to filter the documents from collection
        db.products.find({price:6000}) 

    * If u want to see the documents as serial wise
        db.products.find().pretty()

- Retrieving details from an embedded document 
    ```
        db.products.find({'categories.sub':'smartphones'})
    ```    

- Retrieving details based on an array element
    ```
        db.products.find({'colors':{$in:['black','white']}})

        db.products.find({'colors':{$nin:["gold","rosegold"]}})

        db.products.find({'colors':{$all:['black','white']}}) 

        db.products.find({'colors':{$all:['black','white'],$size:2}}) 

    Note:  
    > db.products.find( {"colors":{$elemMatch:{$eq:"rosegold"}}}, {"prodname":1,"colors":1} ).pretty()
        {
                "_id" : ObjectId("61a3bf0eb6db30c378b51f60"),
                "prodname" : "iphone 7",
                "colors" : [
                        "silver",
                        "black",
                        "gold",
                        "rosegold"
                ]
        }
    ```    

- Using BSON datatypes to retrieve data
    ```
    db.products.find({'price':{$type:'double'}})
    ```

- Logical operator
    ```
    db.products.find({
        $and:[
            {'categories.sub':'smartphones'},
            {'price':{$gte:60001}}
        ]
    }).pretty() 

    db.products.find({
        $or:[
            {'categories.sub':'smartphones'},
            {'price':{$gte:60001}}
        ]
    }).pretty()  
    ```  
   
- Usage of operator ($exists , $elemMatch) 
    ```
        db.products.find( 
            {$and:[
                {"colors":{$elemMatch:{$in:['rosegold','silver']}}},
                {"prodname":{$exists:true}}
            ]},
            {"prodname":1,"manufacturer":1,"colors":1}
        ).pretty() 

        Note: $exists operator only check whether proprty is existing under document or not . But it never check the value ('null','array','string') of property.The value of $exists will be either true or false.  
    ```       

          
        


        
