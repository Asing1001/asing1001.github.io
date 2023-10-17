---
title: mybatis - Cannot determine value type from string, Cannot convert string to Timestamp
date: 2023-10-17 23:43:19
tags: [java, mybatis, error, sql, xml, jdbc, troubleshooting, resultMap]
---

## Problem

These error occurs when selecting columns from the database that don't match the model, for example:

```log
org.springframework.dao.DataIntegrityViolationException: Error attempting to get column 'name' from result set.  Cause: java.sql.SQLDataException: Cannot determine value type from string 'singming'
```

```log
org.springframework.dao.DataIntegrityViolationException: Error attempting to get column 'type' from result set.  Cause: java.sql.SQLDataException: Cannot convert string 'MALE' to java.sql.Timestamp value
```

## Solution

Ensure your SQL query only selects columns that exist in your Java model to avoid type mismatches and data integrity issues.

## Explanation

The error looks ridiculous, it is because mybatis is trying to map results from sql to some fields in the java model. e.g. mapping a `name VARCHAR(255)` to `Date createdTime` even if you add the `jdbcType` mapping in the `<resultMap>`
MyBatis expects a direct mapping between columns in your SQL query and properties in your Java model. If your SQL query selects columns that don't exist in your model, you can encounter type mismatches errors above.

To resolve this:

1. **Review your SQL queries:** Ensure that you only select columns that have corresponding properties in your Java model.

2. **Use aliases:** If your SQL query retrieves columns with different names but equivalent data, use aliases to match them to the model properties.

## Example

```xml
<!-- MyBatis XML Mapper -->

<!-- Result Map -->
<resultMap id="userResultMap" type="User">
    <result property="name" column="name" />
    <result property="age" column="age" />
</resultMap>

<!-- SQL Query -->
<select id="selectUsers" resultMap="userResultMap">
    SELECT name, age FROM users
</select>
```

```java
// Java model
class User {
    private String name;
    private int age;
}
```

In this example, the SQL query and Java model are aligned, resulting in a smooth mapping without type mismatches.
