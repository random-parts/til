---
headline: 'Lucee 5 query returntypes'
date: 2016-06-04
category: lucee-coldfusion
tags:
  - cfx
  - lucee
---

### Query `returntype` returns:

- `array`
- `query`
- `struct`

```java
// return as array
qTemp = queryExecute( sql: "select top 10 * from menu",
    options:{ datasource: "test", returntype: "array" });

dump( qTemp );

// return as struct
qTemp = queryExecute ( sql: "select top 10 * from menu",
    options:{ datasource: "test", returntype: "struct", columnkey: "menu_id" });

dump( qTemp );
```

---
- [source](https://youtu.be/C4MGHlOKzLI?t=49m09s)