# Difference between @RestController and @Controller Annotation in Spring MVC and REST

- @RestController = @Controller + @ResponseBody

<br>

    @Controller
    @ResponseBody
    public class MVCController { }
    
<br>
  
    @RestController
    public class RestFulController { }

- Response from a web application is generally view (HTML + CSS + JavaScript) : @Controller create a Map of model object and find a view
- REST API just return data in form of JSON or XML : @RestController simply return the object and object data is directly written into HTTP response as JSON or XML.

## What are @Controller and @RestController in Spring ?

- A Controller is a class which is responsible for preparing a model Map with data to be displayed by the view as well as choosing the right view itself.

- It can also directly write into response stream by using @ResponseBody annotation and complete the request. It is very useful for responding calls to RESTful web services because their we just return data instead of returning a view

- Now, you don't need to use @Controller and @ResponseBody annotation, instead you can use @RestController 

## Difference between @RestController and @Controller in Spring

- @Controller is used to mark a class as Spring MVC Controller while @RestController is a special controller used in RESTFul web services and the equivalent of @Controller + @ResponseBody.
  
- @RestController is relatively new, added on Spring 4.0. @Controller exists since Spring started supporting annotation, added on Spring 2.5.

- @Controller annotation indicates that the class is a web controller. @RestController annotation indicates that the class is a controller where @RequestMapping methods assume @ResponseBody semantics by default (servicing REST API).

- @Controller is a specialization of @Component annotation while @RestController is a specialization of @Controller annotation :

<br>

    @Target(value=TYPE)
    @Retention(value=RUNTIME)
    @Documented
    @Controller
    @ResponseBody
    public @interface RestController


<br>

    @Target(value=TYPE)
    @Retention(value=RUNTIME)
    @Documented
    @Component
    public @interface Controller
    
- When you mark a class @RestController then every method is written a domain object instead of a view.
  
- You don't need to use @ResponseBody on every handler method once you annotate the class with @RestController :

<br>

    @RestController
    public class Book{    
        @RequestMapping(value={"/book"})
        public Book getBook(){
            //...
            return book;
        }
    }

<br>

    @Controller
    public class Book {
        @RequestMapping(value={"/book"})
        @ResponseBody
        public Book getBook() {
            //...
            return book;
        }
    }

## Sources  
  
- http://javarevisited.blogspot.com/2017/08/difference-between-restcontroller-and-controller-annotations-spring-mvc-rest.html#ixzz531uvQjBh