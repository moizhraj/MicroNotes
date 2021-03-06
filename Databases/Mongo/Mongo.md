# Setup a DB
Create a file called docker-compose.yml
```yaml
version: '3.1'

services:

  mongo:
    image: mongo
    restart: always
    environment:
      MONGO_INITDB_ROOT_USERNAME: root
      MONGO_INITDB_ROOT_PASSWORD: example

  mongo-express:
    image: mongo-express
    restart: always
    ports:
      - 8081:8081
    environment:
      ME_CONFIG_MONGODB_ADMINUSERNAME: root
      ME_CONFIG_MONGODB_ADMINPASSWORD: example
```
---
# Start and Run
```sh
docker-compose up

```
GOTO http://localhost:8081

OR
```
docker exec -it [☢️️️name of docker️ container️️️️☢] bash
```
---
# Upload some data
[Inventory Data](https://raw.githubusercontent.com/mongodb/docs-assets/primer-dataset/inventory.crud.json)

---
```js
mongo --username root --password example
use MikeDB
 db.createCollection("MikeCollection", { capped : true, size : 280000, max : 1000 } )

```

# Mongo Crud
```mongo
db.MikeCollection.insertOne(
   { "item" : "canvas",
     "qty" : 100,
     "tags" : ["cotton"],
     "size" : { "h" : 28, "w" : 35.5, "uom" : "cm" }
   }
)
```

Find All
```
myCursor = db.MikeCollection.find( {} )
```



Find All
```
myCursor = db.MikeCollection.find( {} )
```

Find All
```

 db.MikeCollection.find( {status:"A"} )

```
Aggregate
```
db.MikeCollection.aggregate([    { $match: { status: "A" } },    { $group: { _id: "$item", total: { $sum: "$qty" } } } ])


```


[Docs](https://docs.mongodb.com/guides/)
[Cheat Sheet](https://www.opentechguides.com/how-to/article/mongodb/118/mongodb-cheatsheat.html)

