# Container and Bean Principle

## Bean
> Operated by Spring Container(including initialization, governing)

If you still don't understand what `bean`, please see container part firstly.
`bean` was producted by factory. So we can take it as a abstract production.

In application, it was superclass(precisely interface) of many object, such as : service layer objects, data access layer objects, Hibernate SessionFactory objects, JMS Queue objects and so on.

In my opinion, `bean` is abstract production characters in factory pattern.

### bean initialization
> for Spring IOC container, bean definition described the exact methods and propoties of bean objects. When needed, container get a certain definition of bean, and configurate it by java reflection in order to create a real object.

```java
// This example is about using java reflection to create objects
package com.lzc;
class person {
    private String name;
    private int age;
}
class Test {
    public static void createobj() throws Exception {
        Class classtype = Class.forName('com.lzc.person');
        Object obj = classType.newInstance();
        System.out.println("yes:no?" + (obj instanceof person))
    }
}

```

#### By default constructor
#### By static method
#### By other factories

> these three method to create bean instance maybe not what we focused on. Just use `@Bean`.

### Bean usage
```java
boolean containsBeans(String) //
Object getBean(String) //return bean instance, NosuchBeanDefinitionException
Object getBean(Sting, Class) //return bean instance converted into Class, BeanNotOfRequiredTypeException
```

## container
what is container?
> org.springframework.beans.factory.BeanFactory是Spring IoC容器的实际代表者，IoC容器负责容纳此前所描述的bean，并对bean进行管理。

It is evident that `container` is a implement of [Factory Pattern](../think-in-java.md)
BeanFactory is Spring IOC container representation which manages `bean`.
> BeanFactory is abstract factory.

XMLFactory is an implement of BeanFactory. In my opinion, its aspects contains parse XML file, so it is why we use POM.xml as configuration files.

## Dependency

This concept is easy to understand. codes for example:
```java
public class Company{
    private List<Employee> list;
}
pulic class Employee{
    String name;
}
//This is dependency, company can't init without employees
// Company has a dependency on Employee.
```

### DI(dependency injection)
> 相对于由bean自己来控制其实例化、直接在构造器中指定依赖关系或则类似服务定位器（Service Locator）模式这3种自主控制依赖关系注入的方法来说，控制从根本上发生了倒转，这也正是控制反转（Inversion of Control， IoC） 名字的由来。

1. Setter injection 

> recommended

```java
public class Company {
    //dependency
    private List<Employee> list;
    //a setter method so that the Spring container can 'inject' Employees
    public void setEmployee(List<Employee> list){
        this.list = list;
    }
    //but how to 'inject' was what we can't konw.
}
```

2. Constructor injection
```java
public class Company {
    //dependency
    private List<Employee> list;
    public Company(List<Employee> l) {
        this.list = l;
    }
}
```

### autowire
