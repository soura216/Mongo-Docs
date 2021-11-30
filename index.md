# Index

Always try to implement the index on those key whose has a unique value. 
_id is by default index

- Advantage
    Suppose u have 5 milion documents inside your collection and you want to get a particular document. So in that case you have to wait lots of time to get output because before send the output it read all documents instead of a particular document. However if you use index then u can save the time. 

- Disadvantage
    Index approach only can help you in read operation. But if you want to think write operation through index then it takes a lots of time.

- If u want to know the explain of the execution stats
    ```
    db.products.find({"name":"product4000"}).explain("executionStats")
    ```

- Create index
    ```
    db.products.createIndex({"name":1})
    ```

- List of index
    ```
    db.products.getIndexes()
    ```

- Drop index
    ```
    db.products.dropIndex({"name":1})
    ```