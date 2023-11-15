# learn_mongodb
This repositorty is all about mongodb notes.


Course havving

Course Topics :- pic1

What is MongoDB ? :- Pic_2 What is MongoDB


SQL vs NoSQL (MongoDB) :- Pic_3 SQL vs NoSQL (MOngoDb)



Pic_4 SQL table structure :- Here columns in tables are fixed ,we cannot added new extra column.



Pic_5 NoSQL (MongoDB doc) :- Here we can add or remove fields so its a semistructured or strcutured DB in the form of DOCUMENTS.



MongoDB Terminology:-> Pic_6 MongoDB Terminology
In MongoDB , Database has Collections , this collections can be multiple.
Here in teacher field there is one field "AGE" is not available in second
document , so it is UNSTRUCTURED or SEMISTRCUTRED DB.
While in Product Collection , both documents have different fields hence we can say it is SCHEMALESS structure.


Feature in MongoDB :-> Pic_7 Feature in MongoDB


How MongoDB works ? : -> Pic_8 How MongoDB works
Here front end request to backend
backend create connection with DB
backend request read/write to Storage Engine (name WiredTiger) of MongoDB who handle READ/WRITE DATA files.and Storage Engine request to DB for READ/WRITE.


JSON vs BSON :- > Pic_9 JSON vs BSON
How JSON vs BSON looks ? :- > Pic_10 JSON vs BSON.png

Installation of MongoDB ? :-> Pic_11 Installation


Download below:- 
=> MongoDB community server
https://www.mongodb.com/try/download/community

=> Shell is playground to directly connect with DB (with backend)
https://www.mongodb.com/try/download/shell

=> To import export database
https://www.mongodb.com/try/download/database-tools



To work on MongoDB we need to run the server
Command to run server
>>> mongosh
You will get
Current Mongosh Log ID: 6553886db4682b0d33e5f5fe
Connecting to:          mongodb://127.0.0.1:27017/?directConnection=true&serverSelectionTimeoutMS=2000&appName=mongosh+2.0.2
Using MongoDB:          5.0.8
Using Mongosh:          2.0.2

For mongosh info see: https://docs.mongodb.com/mongodb-shell/

------
   The server generated these startup warnings when booting
   2023-11-14T15:10:46.999+05:30: Access control is not enabled for the database. Read and write access to data and configuration is unrestricted
------

Warning: Found ~/.mongorc.js, but not ~/.mongoshrc.js. ~/.mongorc.js will not be loaded.
  You may want to copy or rename ~/.mongorc.js to ~/.mongoshrc.js.


NOW WE ARE GOOD TO GO FOR CODING...

### Managing DATABASES in MongoDB

1> Creating / Deleting Database
2> Creating / Deleting Collections

:- See list of DATABASE
>>> show dbs
>>> show databases

:- Create or use DB
>>> use <database_name>

:- Deleting DB
>>> db.dropDatabase()


:- Show Collections
>>> show collections

:- Create Collections
>>> db.createCollection('<collection_name>')

:- Deleting Collections
>>> db.<collection-name>.drop()



SEE IMPLEMENTATION:-->
Please enter a MongoDB connection string (Default: mongodb://localhost/):

learnmongodb> show dbs
admin           40.00 KiB
akshaychavhan  108.00 KiB
config         108.00 KiB
local           88.00 KiB
students_api   144.00 KiB
learnmongodb> use learn_mongodb
switched to db learn_mongodb
learn_mongodb> show dbs
admin           40.00 KiB
akshaychavhan  108.00 KiB
config         108.00 KiB
local           88.00 KiB
students_api   144.00 KiB
learn_mongodb> show collections

learn_mongodb> db.createCollection("learn_mongodb1")
{ ok: 1 }
learn_mongodb> show dbs
admin           40.00 KiB
akshaychavhan  108.00 KiB
config         108.00 KiB
learn_mongodb    8.00 KiB
local           88.00 KiB
students_api   144.00 KiB
learn_mongodb> show collections
learn_mongodb1
learn_mongodb> db.learn_mongodb1.drop()
true
learn_mongodb> show collection
MongoshInvalidInputError: [COMMON-10001] 'collection' is not a valid argument for "show".
learn_mongodb> show collections

learn_mongodb> show dbs
admin           40.00 KiB
akshaychavhan  108.00 KiB
config         108.00 KiB
local           88.00 KiB
students_api   144.00 KiB
learn_mongodb> db.createCollection("learn_mongodb1")
{ ok: 1 }
learn_mongodb>
admin           40.00 KiB
akshaychavhan  108.00 KiB
config         108.00 KiB
learn_mongodb    8.00 KiB
local           88.00 KiB
students_api   144.00 KiB
learn_mongodb> db.dropDatabase()
{ ok: 1, dropped: 'learn_mongodb' }
learn_mongodb> show dbs
admin           40.00 KiB
akshaychavhan  108.00 KiB
config         108.00 KiB
local           88.00 KiB
students_api   144.00 KiB




-------------------------------------------------------------

### INSERT OPERATION IN MONGODB

Inserting documents in Mongodb
When use quote and when not use quote
Ordered and Unordered inserts
case sensitive in mongoDB

>>> db.<collection-name>.insertOne({
    field1:value1,
    field2:value2
})

>>> db.<collection-name>.insertMany([
    {field1:value1},
    {field2:value2},
    //...
])


SEE IMPLEMENTATION:-->
learn_mongodb> use learn_mongodb
learn_mongodb> db.learn_mongodb1.insertOne({
... 'name':'akshay', 'age':28})
{
  acknowledged: true,
  insertedId: ObjectId("6553915cb4682b0d33e5f5ff")
}
learn_mongodb> show dbs
admin           40.00 KiB
akshaychavhan  108.00 KiB
config         108.00 KiB
learn_mongodb    8.00 KiB
local           88.00 KiB
students_api   144.00 KiB
learn_mongodb> db.learn_mongodb1.find()
[
  {
    _id: ObjectId("6553915cb4682b0d33e5f5ff"),
    name: 'akshay',
    age: 28
  }
]
learn_mongodb> db.learn_mongodb1.insertMany([{'name':'rajesh','age':20},{'name':"Pushpa","age":23}])
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId("655391feb4682b0d33e5f600"),
    '1': ObjectId("655391feb4682b0d33e5f601")
  }rn_mongodb    8.00 KiB
}ocal           88.00 KiB
learn_mongodb> db.learn_mongodb1.find()
[earn_mongodb> db.dropDatabase()
  {k: 1, dropped: 'learn_mongodb' }
    _id: ObjectId("6553915cb4682b0d33e5f5ff"),
    name: 'akshay',00 KiB
    age: 28an  108.00 KiB
  },ig         108.00 KiB
  {al           88.00 KiB
    _id: ObjectId("655391feb4682b0d33e5f600"),
    name: 'rajesh',
    age: 20
  },
  {
    _id: ObjectId("655391feb4682b0d33e5f601"),
    name: 'Pushpa',
    age: 23
  }
]

-----------------
WHEN TO USE SINGLE OR DUBLE QUOTES :- Pic_12 When to use Quotes

Here is the implementation

learn_mongodb> db.learn_mongodb1.insertOne({"name":"Quote Trial" , age:"None" , subject name : "Englsh"})
Uncaught:
SyntaxError: Unexpected token, expected "," (1:73)

> 1 | db.learn_mongodb1.insertOne({"name":"Quote Trial" , age:"None" , subject name : "Englsh"})
    |                                                                          ^
  2 |

learn_mongodb> db.learn_mongodb1.insertOne({"name":"Quote Trial" , age:"None" , "subject name" : "Englsh"})
{
  acknowledged: true,
  insertedId: ObjectId("655393c3b4682b0d33e5f602")
}
learn_mongodb> db.learn_mongodb1.find()
[
  {
    _id: ObjectId("6553915cb4682b0d33e5f5ff"),
    name: 'akshay',
    age: 28
  },
  {
    _id: ObjectId("655391feb4682b0d33e5f600"),
    name: 'rajesh',
    age: 20
  },
  {
    _id: ObjectId("655391feb4682b0d33e5f601"),
    name: 'Pushpa',
    age: 23
  },
  {
    _id: ObjectId("655393c3b4682b0d33e5f602"),
    name: 'Quote Trial',
    age: 'None',
    'subject name': 'Englsh'
  }
]


-------------------------------------------------------------------------

### Order Unordered inserts  -> Pic_13 Order Unordered inserts.png

If you are inserting 3 data out of which second is not correct.Then you will get error but first document will get added.
Pic_14 Order Unordered inserts.png


Unordered Insers :- If 4 documents are inserted out of which 2nd is wrong then other all will inserted except 2nd.
Pic_15  Unordered inserts.png


Here is the Implementation :- >

test> show dbs
admin           40.00 KiB
akshaychavhan  108.00 KiB
config          72.00 KiB
learn_mongodb   72.00 KiB
local           88.00 KiB
students_api   144.00 KiB
test> use learn_mongodb
switched to db learn_mongodb
learn_mongodb> show collections
learn_mongodb1
learn_mongodb> db.learn_mongodb1.find()
[
  {
    _id: ObjectId("6553915cb4682b0d33e5f5ff"),
    name: 'akshay',
    age: 28
  },
  {
    _id: ObjectId("655391feb4682b0d33e5f600"),
    name: 'rajesh',
    age: 20
  },
  {
    _id: ObjectId("655391feb4682b0d33e5f601"),
    name: 'Pushpa',
    age: 23
  },
  {
    _id: ObjectId("655393c3b4682b0d33e5f602"),
    name: 'Quote Trial',
    age: 'None',
    'subject name': 'Englsh'
  }
]
learn_mongodb> db.learn_mongodb1.insertMany([{name : "India"},{name : "palestine",_id:ObjectId("6553915cb4682b0d33e5f5ff")},{name:"Isreal"}]);
Uncaught:
MongoBulkWriteError: E11000 duplicate key error collection: learn_mongodb.learn_mongodb1 index: id dup key: { _id: ObjectId('6553915cb4682b0d33e5f5ff') }
Result: BulkWriteResult {
  insertedCount: 1,
  matchedCount: 0,
  modifiedCount: 0,
  deletedCount: 0,
  upsertedCount: 0,
  upsertedIds: {},
  insertedIds: {
    '0': ObjectId("65546786f85a83ba10cd6e26"),
    '1': ObjectId("6553915cb4682b0d33e5f5ff"),
    '2': ObjectId("65546786f85a83ba10cd6e27")
  }
}
Write Errors: [
  WriteError {
    err: {
      index: 1,
      code: 11000,
      errmsg: "E11000 duplicate key error collection: learn_mongodb.learn_mongodb1 index: id dup key: { _id: ObjectId('6553915cb4682b0d33e5f5ff') }",
      errInfo: undefined,
      op: { name: 'palestine', _id: ObjectId("6553915cb4682b0d33e5f5ff") }
    }
  }
]
learn_mongodb> db.learn_mongodb1.find()
[
  {
    _id: ObjectId("6553915cb4682b0d33e5f5ff"),
    name: 'akshay',
    age: 28
  },
  {
    _id: ObjectId("655391feb4682b0d33e5f600"),
    name: 'rajesh',
    age: 20
  },
  {
    _id: ObjectId("655391feb4682b0d33e5f601"),
    name: 'Pushpa',
    age: 23
  },
  {
    _id: ObjectId("655393c3b4682b0d33e5f602"),
    name: 'Quote Trial',
    age: 'None',
    'subject name': 'Englsh'
  },
  { _id: ObjectId("65546786f85a83ba10cd6e26"), name: 'India' }
]
learn_mongodb> db.learn_mongodb1.insertMany([{name : "palestine"},{
learn_mongodb> db.learn_mongodb1.insertMany([{name : "Russia"},{name : "palestine",_id:ObjectId("6553915cb4682b0d33e5f5ff")},{name:"Isreal"}],{ ordered:false});
Uncaught:
MongoBulkWriteError: E11000 duplicate key error collection: learn_mongodb.learn_mongodb1 index: id dup key: { _id: ObjectId('6553915cb4682b0d33e5f5ff') }
Result: BulkWriteResult {
  insertedCount: 2,
  matchedCount: 0,
  modifiedCount: 0,
  deletedCount: 0,
  upsertedCount: 0,
  upsertedIds: {},
  insertedIds: {
    '0': ObjectId("655467eef85a83ba10cd6e28"),
    '1': ObjectId("6553915cb4682b0d33e5f5ff"),
    '2': ObjectId("655467eef85a83ba10cd6e29")
  }
}
Write Errors: [
  WriteError {
    err: {
      index: 1,
      code: 11000,
      errmsg: "E11000 duplicate key error collection: learn_mongodb.learn_mongodb1 index: id dup key: { _id: ObjectId('6553915cb4682b0d33e5f5ff') }",
      errInfo: undefined,
      op: { name: 'palestine', _id: ObjectId("6553915cb4682b0d33e5f5ff") }
    }
  }
]
learn_mongodb> db.learn_mongodb1.find()
[
  {
    _id: ObjectId("6553915cb4682b0d33e5f5ff"),
    name: 'akshay',
    age: 28
  },
  {
    _id: ObjectId("655391feb4682b0d33e5f600"),
    name: 'rajesh',
    age: 20
  },
  {
    _id: ObjectId("655391feb4682b0d33e5f601"),
    name: 'Pushpa',
    age: 23
  },
  {
    _id: ObjectId("655393c3b4682b0d33e5f602"),
    name: 'Quote Trial',
    age: 'None',
    'subject name': 'Englsh'
  },
  { _id: ObjectId("65546786f85a83ba10cd6e26"), name: 'India' },
  { _id: ObjectId("655467eef85a83ba10cd6e28"), name: 'Russia' },
  { _id: ObjectId("655467eef85a83ba10cd6e29"), name: 'Isreal' }
]


### Case sensitivity in mongodb
Pic_16 Case sensitivity in mongodb.png


-------------------------------------------------------------------------------------------------

### Reading Operations in MongoDB


Reading documents in MongoDB
Comparison Operators
Logical Operators
Cursors in MongoDB
Elements Operators


-- Finding documents in MongoDB
:- find()
ex:- db.collection_name.find({ key : value})

-- findOne()
ex :- db.collection_name.findOne({ key : value })


---------------------------------------------------------------------------------------------------

### Importing JSON in mongodb

>>> mongoimport jsonfile.json -d database_name -c collection_name

>>> mongoimport jsonfile.json -d database_name -c collection_name --jsonArray (if its an ARRAY)

For example :- 
>>> mongoimport products.json -d shop -c products

>>> mongoimport products.json -d shop -c products --jsonArray




GO WITH FILES  FOLDER WHERE NOTES ARE ADDED.

