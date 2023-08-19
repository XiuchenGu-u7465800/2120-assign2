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







## Task 2.3
### Issues
1. [Parallel bean initialization during startup [SPR-8767]](https://github.com/spring-projects/spring-framework/issues/13410)
Currently, Spring initializes beans in a single thread and in a somewhat random order. This issue helps to describe the issue clearly, easy to understand. And the aim is to have a faster startup, improve the resourece utilization and enhanced the performance.
<img src="image\issue1.png" alt="i1" style="zoom: 50%;" />

2. [Allow creation of Beans that cannot be autowired by type unless qualified #26528](https://github.com/spring-projects/spring-framework/issues/26528)
The current problem in this issue is that, autowiring by type is a convenient feature that allows automatic injection of beans based on their types, which might caused some illegal problem for developers. So it suggests enhancing the Spring framework to enable the creation of beans that cannot be autowired by type unless qualified with specific qualifiers.
<img src="image\issue2.png" alt="i2" style="zoom: 50%;" />

3. [Asynchronous EntityManagerFactory bootstrapping to complete on context refresh completion [SPR-17334]](https://github.com/spring-projects/spring-framework/issues/21868)
It describe a function that need to be implemented, that is  complete the bootstrapping of the **EntityManagerFactory asynchronously**, ensuring it finishes after the context refresh completion.
<img src="image\issue3.png" alt="i3" style="zoom: 50%;" />

4. [Allow to map null value from yaml [SPR-15425] #19986]https://github.com/spring-projects/spring-framework/issues/19986)
Currently, Spring framework might struggle to accurately parse or map null values within the configuration. By allowing the mapping of null values from YAML configurations, this helps avoid parsing errors.
<img src="image\issue4.png" alt="i4" style="zoom: 50%;" />

5. [Bean Validation does not support getters with Optional return type [SPR-15371]](https://github.com/spring-projects/spring-framework/issues/19935)
Currently, the implementation of Bean Validation does not provide support for getters return '**Optional**' types, which propose to able to handle the validation of properties with '**Optional**' return types. The issue will improved the flexibility and ensure the consistency
<img src="image\issue5.png" alt="i5" style="zoom: 50%;" />



### Key elements of an excellent issue(followed by INVEST)



1. **Independent**: The issue should be self-contained, not dependent on other issues, and it should not overlap the concepts.
2. **Negotiable**: The issue should provide enough information so that the developers can understand the issue and make discussion during the development, and it should focus on essence rather than details.
3. **Valuable**: It should improve the products more significant, which need to have value for the customers and users, aligning with the business goals. In addition, it should be more relevant tp split the problems.
4. **Estimable**: Developers should be able to estimate the consumption required based on the provided information, which help to keep the size small, and ensure the developers negotiate correctly.
5. **Small**: The story should focus on a specific problem rather than trying to solve too much at once, so it requires to be scoped appropriately. Otherwise, it is hard for developers to estimate.
6. **Testable**: It should contain clear criteria to verify the problem has been solved correctly, which ensures the developers to completely understand the problem they are going to tackle.
