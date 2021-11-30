# Insert

* One document

```
    db.products.insert({
        prodname: "iphone 7",
        manufacturer: "apple",
        categories: {main:"electronics",sub:"smartphones"},
        year_of_launch: 2017,
        price: 60000,
        colors: ["silver","black","gold","rosegold"]
    })
```    
*or*

```
    db.products.insertOne({
        prodname: "iphone 7",
        manufacturer: "apple",
        categories: {main:"electronics",sub:"smartphones"},
        year_of_launch: 2017,
        price: 60000,
        colors: ["silver","black","gold","rosegold"]
    })
```    

* Multiple documents 

```
    db.products.insertMany([
        {
            prodname: "iphone 7",
            manufacturer: "apple",
            categories: {main:"electronics",sub:"smartphones"},
            year_of_launch: 2017,
            price: 60000,
            colors: ["silver","black","gold","rosegold"]
        },
        {
            prodname: "iphone 8",
            manufacturer: "apple",
            categories: {main:"electronics",sub:"smartphones"},
            year_of_launch: 2019,
            price: 70000,
            colors: ["silver","black","gold","white"]
        },
        {
            prodname: "nokia express music",
            manufacturer: "nokia",
            categories: {main:"electronics",sub:"phones"},
            year_of_launch: 2001,
            price: 3000,
            colors: ["black","white"]
        }
    ])
```    
*or*
```
    db.products.insert([
        {
            prodname: "iphone 7",
            manufacturer: "apple",
            categories: {main:"electronics",sub:"smartphones"},
            year_of_launch: 2017,
            price: 60000,
            colors: ["silver","black","gold","rosegold"]
        },
        {
            prodname: "iphone 8",
            manufacturer: "apple",
            categories: {main:"electronics",sub:"smartphones"},
            year_of_launch: 2019,
            price: 70000,
            colors: ["silver","black","gold","white"]
        },
        {
            prodname: "nokia express music",
            manufacturer: "nokia",
            categories: {main:"electronics",sub:"phones"},
            year_of_launch: 2001,
            price: 3000,
            colors: ["black","white"]
        }
    ])

```    
