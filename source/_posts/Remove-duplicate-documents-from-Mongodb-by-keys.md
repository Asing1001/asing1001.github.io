---
title: Remove duplicate documents from Mongodb by keys
date: 2022-11-17 03:40:20
tags: [Mongodb, index, remove duplicates, unique]
---

## Background

To ensure there is no duplicate documents, we could create an [unique index](https://www.mongodb.com/docs/v5.0/core/index-unique/).
However, it will throw error when there are duplicates entries in the collection:

> MongoDB cannot create a `unique index` on the specified index field(s) if the collection already contains data that would violate the unique constraint for the index.

## Remove the duplicates by keys

```ts
const collection = db.collection('MyCollection');
const operations: Promise<any>[] = [];
console.time('aggregation');

await collection
  .aggregate([
    {
      $group: {
        _id: {
          key1: '$key1',
          key2: '$key2',
        },
        dups: {
          $push: '$_id',
        },
        count: {
          $sum: 1,
        },
      },
    },
    {
      $match: {
        _id: {
          $ne: null,
        },
        count: {
          $gt: 1,
        },
      },
    },
  ])
  .forEach((doc) => {
    console.log(doc);
    doc.dups.slice(1).forEach((duplicateId: string) => {
      operations.push(collection.deleteOne({ _id: duplicateId }));
    });
  });

console.timeEnd('aggregation');

console.time('remove duplicate');
await Promise.all(operations);
console.timeEnd('remove duplicate');
```

## Create the unique index

```ts
await collection.createIndex({ key1: 1, key2: 1 }, { unique: true, name: 'unique_index' });
```
