## Task 1.3
### Creational patterns

1. [Factory Pattern](https://github.com/spring-projects/spring-framework/blob/main/spring-beans/src/main/java/org/springframework/beans/factory/BeanFactory.java)

<img src="image\factory1.png" alt="factory1" style="zoom:50%;" />

<img src="image\fact2.png" alt="fact2" style="zoom: 50%;" />

The *BeanFactory* is one of the implements of Factory Pattern, which provide the interface for creating 'Bean' objects in the '*BeanFactory*', but also allows subclasses such as '*ListableBeanFactory*' to alter the type.

It helps to allow the original dependencies be injected by using the *BeanFactory*, which means that we introduce a third party to handle it, which achieves the effect of loosing coupling.

Besides, we can do some additional process during the instantiation of 'Bean', which only require implementing the '*BeanFactory*' interface, which achieves the effect of high extension.



2. [Singleton Pattern](https://github.com/spring-projects/spring-framework/blob/main/spring-beans/src/main/java/org/springframework/beans/factory/support/AbstractBeanFactory.java#L239-L392)
    <img src="image\single.png" alt="single" style="zoom: 50%;" />

The '*Bean*' object in dependency injection is singleton in default, it happens in the '*getBean*' Function of '*doGetBean*' which import the '*getSingleton*' to create the 'bean'.

This design pattern ensures each class  exists only one object , and provide a global access. However, it does not control the singleton at the constructor level, because the spring manages the arbitrary Java objects 

### Structural patterns

1. [Adapter Pattern](https://github.com/spring-projects/spring-framework/blob/main/spring-webflux/src/main/java/org/springframework/web/reactive/HandlerAdapter.java#L39)

 <img src="image\h1.png" alt="h1" style="zoom: 50%;" />

*DispatcherServlet* send the request to *HandlerAdapter* to process the Handler accroding to the returned handler of *HandlerMapping* .

*HandlerAdapter* run the correspond *Handler*, which will send back a *ModelAndView* to the HandlerAdapter, and the adapter will send it to the 'DispatchServelet'

The *HandlerAdapter* make it easier to extend the Handlers,  and we only need to add a new adapter class to complete the extension of *SpringMVC*.
2. [Decorator Pattern](https://github.com/spring-projects/spring-framework/blob/main/spring-web/src/main/java/org/springframework/web/server/ServerWebExchangeDecorator.java)
 <img src="image\d1.png" alt="d1" style="zoom: 50%;" />


It add additional responsibilities to an object dynamically, which is more flexible than generating subclasses

### Behavioural patterns

1. [Observer Pattern](https://github.com/spring-projects/spring-framework/blob/main/spring-context/src/main/java/org/springframework/context/ApplicationListener.java)

*The event-driven model* is implemented by using *Observer pattern* in Spring, which frequently used to implement the 'listener' . It consists of 3 part,

* Event Source
<img src="image\o1.png" alt="o1" style="zoom: 50%;" />

* Event Listener
<img src="image\o2.png" alt="o2" style="zoom: 50%;" />

* Event Source 
<img src="image\o3.png" alt="o3" style="zoom: 50%;" />




2. [Strategy Pattern](https://github.com/spring-projects/spring-framework/blob/main/spring-core/src/main/java/org/springframework/core/io/UrlResource.java)

The *Resource* Interface in the Spring framework enhances resource access capabilities. It serves as a powerful tool for interacting with resources,  and it is a obvious strategy pattern.