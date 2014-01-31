Java-Spring-LAB
===============

This project is a reference Web Application working as a personal laboratory in order to test spring features. 

Spring api for this application:
- spring-context 4.0.1.RELEASE
- spring-webmvc 4.0.1.RELEASE
- spring-web 4.0.1.RELEASE

* Priorities of dependencies resolution

When there are both implementations of a concrete service interface, one defined using annotation and another one using spring configuration. Which implementation will Spring use to resolve that interface?

Let's start:

1.- In Java-Spring-LAB/src/main/com/java/spring/lab/controllers/ServiceController.java, there is a field using an autowired annotation to resolve the Service implementation.
2.- In Java-Spring-LAB/src/main/com/java/spring/lab/services/Service.java is the interface to resolve.
3.- In Java-Spring-LAB/src/main/com/java/spring/lab/services/impl/NameService.java is the implementation that is resolved by autoscan components (by including the Service annotation).
4.- In Java-Spring-LAB/src/main/resources/spring/mvc-config.xml, there is a "service" bean with MyNameService reference implementation which is in Java-Spring-LAB/src/main/com/java/spring/lab/services/impl/MyNameService.java.

In the current status, with the commented bean in mvc-config.xml, the NameService class is properly resolved due to autoscan components tag is set in such spring properties.

When user uncomments the bean of MyNameService (important to specify the id), the MyNameService class is used insteads of NameService class.

Therefore, the XML settings prioritizes its configuration againts annotations.
 
