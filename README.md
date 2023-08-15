# MongoDB Shell Cheat Sheet

A quick reference guide for common MongoDB shell commands and operations.

## Table of Contents
- [Connecting to MongoDB](#connecting-to-mongodb)
- [Basic Commands](#basic-commands)
- [CRUD Operations](#crud-operations)
- [Query Operators](#query-operators)
- [Indexing](#indexing)
- [Aggregation Framework](#aggregation-framework)
- [Miscellaneous](#miscellaneous)

## Connecting to MongoDB

```shell
mongo --host <hostname> --port <port> -u <username> -p <password> --authenticationDatabase <authDB>
```

## Connecting to MongoDB

```shell
show dbs                    # List all databases
use <db_name>               # Switch to a specific database
db                          # Show the current database
show collections            # List collections in the current database
```

## CRUD Operations

```shell
# Insert operations
db.<collection_name>.insertOne({document})
db.<collection_name>.insertMany([{doc1}, {doc2}])

# Retrieve operations
db.<collection_name>.find()
db.<collection_name>.findOne({query})
db.<collection_name>.find({query})

# Update operations
db.<collection_name>.updateOne({query}, {$set: {update}})
db.<collection_name>.updateMany({query}, {$set: {update}})

# Delete operations
db.<collection_name>.deleteOne({query})
db.<collection_name>.deleteMany({query})
```

## Query Operators

```shell
$eq     # Equal
$ne     # Not Equal
$gt     # Greater Than
$lt     # Less Than
$gte    # Greater Than or Equal
$lte    # Less Than or Equal
$in     # Match any value in an array
$nin    # Not match any value in an array
$and    # Logical AND
$or     # Logical OR
```

## Indexing

```shell
db.<collection_name>.createIndex({field: 1})    # Create ascending index
db.<collection_name>.createIndex({field: -1})   # Create descending index
db.<collection_name>.getIndexes()               # List all indexes in a collection
```

## Aggregation Framework

```shell
db.<collection_name>.aggregate([
    { $match: { field: value } },           # Filtering documents
    { $group: { _id: "$field", count: { $sum: 1 } } },   # Grouping documents
    { $sort: { count: -1 } },               # Sorting documents
    { $project: { _id: 0, field: 1 } }      # Projecting fields in output
])
```

## Miscellaneous

```shell
db.dropDatabase()             # Delete the current database
db.<collection_name>.drop()   # Delete a collection
```
