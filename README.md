[![](https://jitpack.io/v/juliofalbo/j-api-filter.svg)](https://jitpack.io/#juliofalbo/j-api-filter)

# JApiFilter

The purpose of JApiFilter is a simplification of the use of REST for filters by parameters!

## Requirements

   * Spring Boot 2.x
   * Java 8

## Add in your project
Use [*JitPack*] (https://jitpack.io/#juliofalbo/j-api-filter/-SNAPSHOT)

###  Maven

```
<repositories>
  <repository>
      <id>jitpack.io</id>
      <url>https://jitpack.io</url>
  </repository>
</repositories>

...

<dependency>
    <groupId>com.github.juliofalbo</groupId>
    <artifactId>j-api-filter</artifactId>
    <version>-SNAPSHOT</version>
</dependency>
```

### Gradle

```
allprojects {
  repositories {
    ...
    maven { url 'https://jitpack.io' }
  }
}

...

dependencies {
      implementation 'com.github.juliofalbo:j-api-filter:-SNAPSHOT'
}
```

## How to use?

*First it is important to know that JApiFilter is based on the Spring Data Specification.*

### Now let's go!

# Repository
The first thing to do is to implement the **[JpaSpecificationExecutor](https://docs.spring.io/spring-data/jpa/docs/current/api/org/springframework/data/jpa/repository/JpaSpecificationExecutor.html)** interface in your repository, so you will have access to the **findAll(Specification <T> spec)** method 

# Builder
**Using the JApiSpecificationBuilder class is very simple.**

To create a specification based on some entity, simply use the *createFiltersByEntity* method, as in the example below:

Ex:
```
Specification<YourEntity> specification = JApiSpecificationBuilder.init()
                .createFiltersByEntity(yourEntity, JApiOperationEnum.EQUAL)
                .buildSpec();
```

To create specific filters, the builder provides methods to create filters according to a particular operation:

* withEqualFilter
* withBiggerFilter
* withSmallerFilter
* withLikeFilter
* withCustomFilter

Ex:
```
Specification<YourEntity> specification = JApiSpecificationBuilder.init()
                .withEqualFilter("yourVarName", yourObject)
                .withBiggerFilter("yourVarName", yourObject)
                .withSmallerFilter("yourVarName", yourObject)
                .withLikeFilter("yourVarName", yourObject)
                .withCustomFilter("yourVarName", yourObject, JApiOperationEnum.[yourChoise])
                .buildSpec();
```

# Operations
Currently available operations are:

* EQUAL
* BIGGER
* SMALLER
* LIKE

## Current Version
0.1

___

##### [Júlio Falbo](http://juliofalbo.tech)
