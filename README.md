# Annotations

2.@Autowired
=> Performs byType,byName,Constructor mode of autowiring(detecting the
dependent bean dynamically without using <property>
and <constructor-arg> tags)

=> Can be applied on field level(instance variables),constructor,setter
methods.
=> It cannot be used to inject values to simple properties, can be used to
injection values only to Object type/ref type.
=> Through annotation support, without setter/constructor still injection can be
done through "instance variables", where spring
uses "Reflection API" to access private properties of a class.
=> Default Autowiring is based on byType.

@Qualifer is having high priority than primary, so bDart object will be
injected to Flipkart class.

It can be applied at the constructor level also.
public class Flipkart {
@Autowired |=>Dependant
Object
public Flipkart(@Qualifier("fFlight") Courier courier) {
this.courier = courier;
System.out.println("Flipkart:: One Param constructor...");
}
}
Performing Setter injection using @Autowired
public class Flipkart{
@Autowired |=> Dependant Object
public void setCourier(@Qualifier("bDart") Courier courier) {
this.courier = courier;
System.out.println("Flipkart.setCourier():: Setter Injection");
}
}


SteroType Annotation
--------------------
=> We have multiple annotations with similar behaviour.. having minor differences
so they are called as "Stereotype annotations".
@Component ====> To configure java class as Spring bean (bean will be created and it is managed by IOC container)

@Service =====> @Component + also makes the service class by giving
Transaction management support(Sprign AOP)

@Repository =====> @Component + also makes the DAO class by Exception
propogation facilities(SQLException to Spring specific Exception)

@Controller =====> @Component + also makes the Controller class getting the
facility of handling HttpRequests.

These stereo-annotations should be applied only at the class level.
-----------------------------------------------------------------------------------------------------

Annotations used for lazy loading, keeping the beans in particular scope, and getting values from properties file
==================================================================================================================
@Lazy ===> On the bean it would perform Lazy Loading
@Scope ==> It specifies the scope in which the bean should be kept.
@PropertySource(value="") => It specifies the location from where the properties file data should be taken.
@Value("${fk.info.url}") ===> to inject value to variable from properties file























1. @Required(Deprecated from 5.1V of Spring)

=> While working with parameterized constructor injection we must

configure all params of that constructor injection.
if we fail to do it would result in "Exception".

=> This restriction is not available if we work with "Setter

Injection".

=> To bring such restriction on choice of our bean properties through

Setter injection, we need to go for
@Required.

Note:
The entire functionality of @Required annotation is placed inside a ready made
class called "RequiredAnnotationBeanPostProcessor".
So to use annotations in our application we need to configure the above class as
"Spring bean".
Configuring BeanPostProcessor for every annoation seperately is a complex process,
to overcome this problem just use
<context:annotation-config/> in spring bean configuration file.
The above code in the configuration file would activate the following annotations
@Required,@Autowired,@PostConstruct,@PreDestroy,@Resource,.....
Note:
@Required is deprecated in Spring5.1, saying to go for consturctor injection in

order to add restrictions on injection.
