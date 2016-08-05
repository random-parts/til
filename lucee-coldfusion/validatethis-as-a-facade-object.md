---
headline: 'ValidateThis: Using as a Facade Object'
date: 2016-03-18
category: lucee-coldfusion
tags:
  - validateThis
  - cfx
  - mvc
---

Using ValidateThis with MVC + Injection Framework ([DI/1])

- [ValidateThis Config Struct]

```java
// application.cfc

// DI/1 config struct
diConfig:  {
              loadListener = beanConfig
            }

 // BEAN LOADER - loadListener
public void function beanConfig ( bf ) {
    bf.declareBean( "Validator", "ValidateThis.ValidateThis", true,
                   { ValidateThisConfig =
                      {
                        defaultFailureMessagePrefix = "",
                        definitionPath = "/source/rules/"
                      }
                    });
}
```

- Inject into controller and use to validate struct/objects
- See [ValidateThis Facade Object] for more info

```java
// controller.cfc

component accessors = true {
  property Validator;

  public void function foo () {
    result = Validator.validate( myObject, "rules-def", "context" )
  }
}
```


[DI/1]: https://github.com/framework-one/di1
[ValidateThis Config Struct]: https://web.archive.org/web/20141006215643/http://www.validatethis.org/docs/wiki/ValidateThisConfig_Struct.cfm
[ValidateThis Facade Object]: https://web.archive.org/web/20141007151541/http://www.validatethis.org/docs/wiki/ValidateThis_Facade_Object.cfm