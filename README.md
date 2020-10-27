# Custom Dependency Injection framework

It is very small project, that shows, how you can build your own dependency injection framework.

It suitable for **constructor** and **field** injection.

- You can find the framework itself under "com.demo.framework" package.

### How you can use

##### 1. Creating class as desired (you can find example under com.demo.framework.examples package

##### 2. Add **@OwnInject** annotation to constructor or field.

```java
public class ControllerObject {
	private String ControllerName = "Default Controller Name";
	
	@CustomInject
	ServiceObject serviceObject;
	
	@CustomInject
	public ControllerObject(ServiceObject serviceObject)
	{
		this.serviceObject = serviceObject;
	}
}
```
##### 3. Use **CustomInjector** to get your injected class.

### How it works

The two main classes are **CustomInjector** and **customDependencyInjector**.
 
* The **CustomInjector** will scan the project for classes which are compiled (.class files).
* The **customDependencyInjector** performs the injection via java reflection. It checks that the constructor or fields are annotated with **@CustomInject** annotation.
 
### Design consideration
To perform Dependency Injection as it is in Spring, make the dependency injection as much simple as possible

### Limitation
Currently, the framework only can perform injection on constructor and fields, other annotations e.g Bean, ... are not available
And function of using configuration is not available either
Spring bean scope singleton and prototype are not implemented yet.
Unit tests are currently empty.
Currently, I don't know how to use this framework like a library, import to a specific Spring project, and to make it run at the starting point of Spring Application.