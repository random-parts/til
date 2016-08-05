---
headline: 'ValidateThis: Validating nested objects'
date: 2016-03-18
category: lucee-coldfusion
tags:
  - validateThis
  - cfx
  - lucee
---

Trying to validate `user` object containing a child object `contact`

```java
// user.cfc

property name = "id"        default = "";
property name = "contact"   // nested object
```

- Use: `"params": [{"name": "objectType", "value": "contact"}]` 

This tells ValidateThis to use the JSON Rules defined in `contact.json` for `contact` object

```java
// user.json - Rules Definition File

{"name" : "contact", "desc": "contact object"
  "rules" : [ 
            {"type": "isValidObject", "context": "", "failureMessage": "",
            "params": [{"name": "objectType", "value": "contact"}]
            }]
```

---
- [archive source](https://web.archive.org/web/20141006225333/http://www.validatethis.org/docs/wiki/Validation_Types_Supported_By_ValidateThis.cfm#IsValidObject)