
# Eureka Server

This is a server for registration and discovery of services in the microservice architecture.

## Running Eureka locally
Eureka server is a [Spring Boot](https://spring.io/guides/gs/spring-boot) application built using [Maven](https://spring.io/guides/gs/maven/). You can build a jar file and run it from the command line:


```
git clone https://github.com/NdiranguMuchai/eureka-server.git
cd eureka-server
./mvnw package
java -jar target/*.jar
```

You can then access eureka here: http://localhost:8761/

<img width="1042" alt="eureka-server" src="https://cloud.githubusercontent.com/assets/838318/19727082/2aee6d6c-9b8e-11e6-81fe-e889a5ddfded.png">

Or you can run it from Maven directly using the Spring Boot Maven plugin. If you do this it will pick up changes that you make in the project immediately (changes to Java source files require a compile as well - most people use an IDE for this):

```
./mvnw spring-boot:run
```

### Services registrered
Two services have been registered to the architecture

* [Item catalogue](https://github.com/NdiranguMuchai/item-catalogue) running on port `2222`
* [Edge service](https://github.com/NdiranguMuchai/edge-service) running on port `1103`

Use the same commands to run the services as the one you used 
to run eureka i.e either by building a `jar` or using the `Maven` plugin.

Once the services are running you can confirm their successful registration on the eureka server

<img width="1042" alt="eureka-server" src="https://cloud.githubusercontent.com/assets/838318/19727082/2aee6d6c-9b8e-11e6-81fe-e889a5ddfded.png">

### Service Interaction
* `Item catalogue` displays a list of several sports items in `Json` on http://localhost:2222/items
* `Edge service` then filters through the list of items on `Item catalogue` and chooses a select few top brands only if `Item catalogue` service is running and returns a list in `Json` on http://localhost:1103/top-brands