---
title: A Quick Intro to DynamoDB
tags: AWS, Programming, DynamoDB
category: AWS
excerpt: DynamoDB is part of the Amazon web services family and is a NoSQL database service that is fast and has predictable performance with scalability.
created: 2021-02-04
image: ./images/intro_dynamodb.png
image_caption: 
author: author1
---

# What is DynamoDB?

DynamoDB is part of the Amazon web services family and is a NoSQL database service that is fast and has predictable performance with scalability. DynamoDB reduces the burdens of operating and scaling a distributed database so that you as the developer don't have to worry about hardware provisioning, setup/configuration, replication, software patching, or cluster scaling.

On top of lifting those burdens it also offers a few other positive benefits. The first benefit is that you can create database tables that can store and retrieve any amount of data and serve any level of request traffic. You can also scale up or scale down your tables’ throughput capacity without any downtime or performance degradation. The second benefit is that DynamoDB offers an on-demand backup capability. This allows you to create full backups of your tables for retention and archival. The last benefit that I will mention here is that DynamoDB allows you to delete expired items from tables automatically which helps to reduce your storage usage and the cost of storing that data.

&nbsp;

# What is the basic terminology that I should know when using DynamoDB?

There are really five essential terms that you should know when starting to work with DynamoDB. Those terms are: `Table`, `Item`, `Attribute`, `Primary Key` and `Secondary Indexes`.

### Table
A **`Table`** in its simplest definition, is a collection of data. A table in DynamoDB is similar to a table in a relational database but has some key usage differences. For example, when working with DynamoDB you will generally have a single table for all your data instead of separate tables for each entity in a relational database. I’ll be writing an additional article that will go over this in more detail.

### Item
An **`Item`** is a group of attributes that is uniquely identifiable among all of the other items. If you are used to relational databases, this is the equivalent of a row in a relational database. Each Table in DynamoDB will contain zero or more items. If you look at the JSON below, this would be a very basic example of an `Item` in DynamoDB.

### Attribute
An **`Attribute`** is a data element and something that does not need to be broken down any further. Each item is composed of one or more attributes. An attribute can have one of the following types: String, Number, Boolean, Binary, Null, List, Map or Set.

### Primary Key
The **`Primary Key`** is used to uniquely identify each item in the table, so that no two items can have the same key. This primary key has to be included on every item and has to be unique to that item. When you create a new table, in addition to the table name, you will also have to specify the primary key of the table. Taking a look at the JSON below, `PersonID` would be the `Primary Key`. DynamoDB supports two different types of primary keys: `Partition Key` and `Partition Key and Sort Key`. 

A `Partition Key` is a simple primary key, composed of only one attribute. In a table that has only a partition key, no two items can have the same partition key value. 

A `Partition key and sort key` is composed of two attributes: a partition key, and a sort key. If a table has a partition key and a sort key, it is then possible for two items to have the same partition key value. However, those two items must have different sort key values.

### Secondary Index
A **`Secondary Index`** lets you query the data in the table using an alternate key, in addition to queries against the primary key. You are basically telling DynamoDB to create a copy of the table using different columns as the primary key. They are going to copy that data into this secondary index and then you can query that secondary index as if it was your primary table. You are not required to use indexes, but they do give your applications more flexibility when querying your data. When it comes to secondary indexes, DynamoDB supports two different kinds: `Global secondary index` and `Local secondary index`.

- The `Global Secondary Index` is an index with a partition key and sort key that can be different from those on the table.

- The `Local Secondary Index` is an index that has the same partition key as the table, but a different sort key.


&nbsp;


```json
{
    "PersonID": 101,
    "LastName": "Doe",
    "FirstName": "John",
    "Address": {
        "Street": "123 Banana St",
        "City": "Anytown",
        "State": "NC"
    }
}
```


# Continue Learning

While this is just a very brief overview of what DynamoDB is and the terminology that you should know, there is still much more to learn. I will be going more in depth in future articles, but until then please check out these links to continue learning.

&nbsp;
### Amazon Resources

https://aws.amazon.com/dynamodb/

https://aws.amazon.com/dynamodb/getting-started/

https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/GettingStartedDynamoDB.html

### Podcasts and Other Articles

https://fullstackradio.com/139

https://www.dynamodbguide.com/

https://www.alexdebrie.com/posts/dynamodb-single-table/






