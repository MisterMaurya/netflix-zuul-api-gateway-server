# Netflix-zuul-api-gateway-server

## application.properties

```java
spring.application.name=netflix-zuul-api-gateway-server
server.port=8765
eureka.client.service-url.default-zone=http://localhost:8761/eureka

```

## Main Class

```java

// ENABLE ZUUL API GATEWAY SEVER
@EnableZuulProxy
@SpringBootApplication
// TO CONNECT WITH DISCOVERY SERVER
@EnableDiscoveryClient
public class NetflixZuulApiGatewayServerApplication {

    public static void main(String[] args) {
        SpringApplication.run(NetflixZuulApiGatewayServerApplication.class, args);
    }

}

```

## pom.xml

```java
<!--TO CONNECT WITH DISCOVERY SERVER-->
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-netflix-eureka-client</artifactId>
</dependency>

<!--TO CREATE ZUUL API GATE WAY-->
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-netflix-zuul</artifactId>
</dependency>

<!--TO TRACE THE REQUEST WITH UNIQUE ID-->
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-sleuth</artifactId>
</dependency>


<!--THE BELOW TWO DEPENDENCY HELPS US SEND THE LOGS IN ZIPKIN SERVER-->
<!--REQUIRED STEPS-->
<!--
        1. Install Rabbit MQ
        2. Download Zipkin server jar and RUN it.
        THEN ALL THE LOG WILL BE CAPTURE IN Zipkin server
        -->
<!-- <dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-zipkin</artifactId>
</dependency>

<dependency>
    <groupId>org.springframework.amqp</groupId>
    <artifactId>spring-rabbit</artifactId>
</dependency>-->

```

## API Call
```java
localhost:8765/<anothorApplicationName>/<URI>
localhost:8765/currency-exchange-service/currency-exchange/from/{from}/to/{to}
```
    