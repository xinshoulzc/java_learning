# Spring-boot annotation
## [Java Prefined Annotation](https://docs.oracle.com/javase/tutorial/java/annotations/predefined.html)
* `@SpringBootApplication`

    > equal to `@Configuration` + `@EnableAutoConfiguration` + `@ComponentScan`
    > > `@EnableAutoConfiguration` (class-level annotation)
    > i don't know more details 

* `@RestController`
    
    > class annotaion
    > not understand
    > Spring will consider class which using `@RestController` when handling incoming web requests

* `@ResponseBody` `@RequestBody`

    > `@RequestBody` 将HTTP请求正文转换为适合的HttpMessageConverter对象。
    > `@ResponseBody` 将内容或对象作为 HTTP响应正文返回，并调用适合HttpMessageConverter的Adapter转换对象，写入输出流。

* `@RequestMapping`
        
    > method annotation also class annotation
    > this annotation provides 'routing' information. In following codes, It is telling Spring that any HTTP request with the path "/" should be mapped to the `home` method
```java
    @RequestMapping("/")
    String home() {
        return "Hello World!";
    }
```
    

* `@EnableConfigurationProperties(StorageProperties.class)`

    > 

* `@Bean`

    >

* `@Autowired`

    > ## `@Autowired` annotation on setter method
    > By using `@Autowired`, you can get rid of <property> elements in XML configuration file. It tries to perform **byType** autowiring on the method.
    > ## `@Autowired` annotation on properties
    > By using `@Autowired`, you can get rid of the setter methods
    > ## `@Autowored` annotation on constrcutors
    > By using `@Autowired`, you can get rid of <constructor-arg> elements in XML configuration file.

* `@Override`(java prefined)

    > this annotation informs the compiler that the element is meant to override an element declared in a superclass(superclass don't contain interface).

* `@Documented`(java prefined)

    > this indicates that whenever the specified annotation is used those elements should be documented using the javadoc tool(you may be confused about what is javadoc, it doesn't matter. Just reckon it a test tool)

