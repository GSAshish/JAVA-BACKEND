- @component annotation is used to tell that this is a bean

```java
@Component // rename @Component("stu")
class Student{
	@value("Ashish"); // to pass value
	 private String name;
	 @value("Maths")
	 private String subject;
	 @Value("#{'${myList}'.split(',')}") // Use ',' as the delimiter if your values are comma-separated 
	 private List<String> myList;
}
```
in config file
```xml
<context:component-scan base-package=""/>
<util:list id="myList">
    <value>Value 1</value>
    <value>Value 2</value>
    <value>Value 3</value>
</util:list>

```
main
```java
import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.AnnotationConfigApplicationContext;

public class MainApp {
    public static void main(String[] args) {
        ApplicationContext context = new AnnotationConfigApplicationContext("com.example"); // Replace with your package name

        // Retrieve the Student bean from the context
        // stu in renamed as stu
        Student student = context.getBean("Student",Student.class);

        // Access the properties of the Student bean
        System.out.println("Name: " + student.getName());
        System.out.println("Subject: " + student.getSubject());
    }
}

```
