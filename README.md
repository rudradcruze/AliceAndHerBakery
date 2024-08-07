# AliceAndHerBakery Project

AliceAndHerBakery is a Spring Boot application designed for conditional property, how beans works and environment variables.

## Project Structure
- **src/main/java/org/rudradcruze/aliceandherbakery/CakeBaker.java**: Contains the `CakeBaker` class responsible for baking the cake.
- **pom.xml**: Maven configuration file for managing project dependencies and build plugins.
- **src/main/resources/application.properties**: Configuration file for setting application properties.

## Dependencies
The project uses the following dependencies:
- `spring-boot-starter-web`: For building web applications.
- `spring-boot-starter-test`: For testing the application.

## Configuration
The `application.properties` file contains the following properties:
- `spring.application.name`: Name of the application.
- `flavor.type`: Type of frosting flavor.
- `syrup.type`: Type of syrup.

## How to Run
1. Ensure you have Java 21 and Maven installed.
2. Navigate to the project directory.
3. Run the application using the following command:
   ```sh
   mvn spring-boot:run
   ```

## Overview of the Code

The provided code snippets demonstrate the use of Spring Boot's `@ConditionalOnProperty` annotation to conditionally create beans based on environment variables specified in the `application.properties` file. Here's a detailed explanation:

1. **`@ConditionalOnProperty` Annotation**:
    - This annotation is used to conditionally enable or disable a Spring bean based on the presence and value of a specific property in the `application.properties` file.
    - It takes two main attributes:
        - `name`: The name of the property to check.
        - `havingValue`: The value that the property must have for the bean to be created.

2. **Environment Variables**:
    - Environment variables are specified in the `application.properties` file.
    - For example:
      ```properties
      syrup.type=chocolate
      flavor.type=strawberry
      ```

3. **Beans**:
    - **`ChocolateSyrup`**:
        - This bean is created only if the `syrup.type` property is set to `chocolate`.
        - It implements the `Syrup` interface and provides the `getSyrupType` method.
    - **`StrawberrySyrup`**:
        - This bean is created only if the `syrup.type` property is set to `strawberry`.
        - It implements the `Syrup` interface and provides the `getSyrupType` method.
    - **`StrawberryFrosting`**:
        - This bean is created only if the `flavor.type` property is set to `strawberry`.
        - It implements the `Frosting` interface and provides the `getFrostingType` method.

### Example `application.properties`:
```properties
spring.application.name=AliceAndHerBakery
flavor.type=strawberry
syrup.type=chocolate
```

### Example Beans:
```java
@Component
@Primary
@ConditionalOnProperty(name = "syrup.type", havingValue = "chocolate")
public class ChocolateSyrup implements Syrup {
    @Override
    public String getSyrupType() {
        return "Chocolate Syrup";
    }
}
```

```java
@Component
@ConditionalOnProperty(name = "syrup.type", havingValue = "strawberry")
public class StrawberrySyrup implements Syrup {
    @Override
    public String getSyrupType() {
        return "Strawberry Syrup";
    }
}
```

```java
@Component
@ConditionalOnProperty(name = "flavor.type", havingValue = "strawberry")
public class StrawberryFrosting implements Frosting {
    @Override
    public String getFrostingType() {
        return "Strawberry Frosting";
    }
}
```

## 🚀 About Me

Tech-savvy learner/programmer pushing boundaries of online tech. Passionate about new tools, seeking challenges to advance skills.

## 🔗 Social Links

![Name](https://img.shields.io/badge/Name-Francis%20Rudra%20D%20Cruze-yellowgreen?style=for-the-badge)
[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/rudradcruze)
[![twitter](https://img.shields.io/badge/twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white)](https://twitter.com/rudradcruze)
[![Facebook](https://img.shields.io/badge/facebook-4267B2?style=for-the-badge&logo=facebook&logoColor=white)](https://facebook.com/rudradcruze)
[![francisrudra@gmail.com](https://img.shields.io/badge/gmail-4267B2?style=for-the-badge&logo=gmail&logoColor=white)](mailto:francisrudra@gmail.com)