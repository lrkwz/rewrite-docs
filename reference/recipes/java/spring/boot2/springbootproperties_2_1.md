# Migrate Spring Boot properties to 2.1

**org.openrewrite.java.spring.boot2.SpringBootProperties\_2\_1**

_Migrate properties found in `application.properties` and `application.yml`._

### Tags

* spring
* boot

## Recipe source

[GitHub](https://github.com/openrewrite/rewrite-spring/blob/main/src/main/resources/META-INF/rewrite/spring-boot-21-properties.yml), [Issue Tracker](https://github.com/openrewrite/rewrite-spring/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite.recipe/rewrite-spring/5.1.7/jar)

* groupId: org.openrewrite.recipe
* artifactId: rewrite-spring
* version: 5.1.7

{% hint style="info" %}
This recipe is composed of more than one recipe. If you want to customize the set of recipes this is composed of, you can find and copy the GitHub source for the recipe from the link above.
{% endhint %}

## Usage

This recipe has no required configuration options. It can be activated by adding a dependency on `org.openrewrite.recipe:rewrite-spring:5.1.7` in your build file or by running a shell command (in which case no build changes are needed): 
{% tabs %}
{% tab title="Gradle" %}
1. Add the following to your `build.gradle` file:
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("6.6.2")
}

rewrite {
    activeRecipe("org.openrewrite.java.spring.boot2.SpringBootProperties_2_1")
}

repositories {
    mavenCentral()
}

dependencies {
    rewrite("org.openrewrite.recipe:rewrite-spring:5.1.7")
}
```
{% endcode %}
2. Run `gradle rewriteRun` to run the recipe.
{% endtab %}

{% tab title="Gradle init script" %}
1. Create a file named `init.gradle` in the root of your project.
{% code title="init.gradle" %}
```groovy
initscript {
    repositories {
        maven { url "https://plugins.gradle.org/m2" }
    }
    dependencies { classpath("org.openrewrite:plugin:6.6.2") }
}
rootProject {
    plugins.apply(org.openrewrite.gradle.RewritePlugin)
    dependencies {
        rewrite("org.openrewrite.recipe:rewrite-spring:5.1.7")
    }
    rewrite {
        activeRecipe("org.openrewrite.java.spring.boot2.SpringBootProperties_2_1")
    }
    afterEvaluate {
        if (repositories.isEmpty()) {
            repositories {
                mavenCentral()
            }
        }
    }
}
```
{% endcode %}
2. Run `gradle --init-script init.gradle rewriteRun` to run the recipe.
{% endtab %}
{% tab title="Maven POM" %}
1. Add the following to your `pom.xml` file:
{% code title="pom.xml" %}
```xml
<project>
  <build>
    <plugins>
      <plugin>
        <groupId>org.openrewrite.maven</groupId>
        <artifactId>rewrite-maven-plugin</artifactId>
        <version>5.17.0</version>
        <configuration>
          <activeRecipes>
            <recipe>org.openrewrite.java.spring.boot2.SpringBootProperties_2_1</recipe>
          </activeRecipes>
        </configuration>
        <dependencies>
          <dependency>
            <groupId>org.openrewrite.recipe</groupId>
            <artifactId>rewrite-spring</artifactId>
            <version>5.1.7</version>
          </dependency>
        </dependencies>
      </plugin>
    </plugins>
  </build>
</project>
```
{% endcode %}
2. Run `mvn rewrite:run` to run the recipe.
{% endtab %}

{% tab title="Maven Command Line" %}
{% code title="shell" %}
You will need to have [Maven](https://maven.apache.org/download.cgi) installed on your machine before you can run the following command.

```shell
mvn -U org.openrewrite.maven:rewrite-maven-plugin:run -Drewrite.recipeArtifactCoordinates=org.openrewrite.recipe:rewrite-spring:RELEASE -Drewrite.activeRecipes=org.openrewrite.java.spring.boot2.SpringBootProperties_2_1
```
{% endcode %}
{% endtab %}
{% tab title="Moderne CLI" %}
You will need to have configured the [Moderne CLI](https://docs.moderne.io/moderne-cli/cli-intro) on your machine before you can run the following command.

{% code title="shell" %}
```shell
mod run . --recipe SpringBootProperties_2_1
```
{% endcode %}
{% endtab %}
{% endtabs %}

## Definition

{% tabs %}
{% tab title="Recipe List" %}
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `server.jetty.max-http-post-size`
  * newPropertyKey: `server.jetty.max-http-form-post-size`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `server.servlet.path`
  * newPropertyKey: `spring.mvc.servlet.path`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `server.tomcat.max-http-header-size`
  * newPropertyKey: `server.max-http-header-size`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `server.tomcat.max-http-post-size`
  * newPropertyKey: `server.tomcat.max-http-form-post-size`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.activemq.pool.maximum-active-session-per-connection`
  * newPropertyKey: `spring.activemq.pool.max-sessions-per-connection`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.artemis.pool.maximum-active-session-per-connection`
  * newPropertyKey: `spring.artemis.pool.max-sessions-per-connection`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.kafka.admin.ssl.keystore-location`
  * newPropertyKey: `spring.kafka.admin.ssl.key-store-location`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.kafka.admin.ssl.keystore-password`
  * newPropertyKey: `spring.kafka.admin.ssl.key-store-password`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.kafka.admin.ssl.truststore-location`
  * newPropertyKey: `spring.kafka.admin.ssl.trust-store-location`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.kafka.admin.ssl.truststore-password`
  * newPropertyKey: `spring.kafka.admin.ssl.trust-store-password`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.kafka.consumer.ssl.keystore-location`
  * newPropertyKey: `spring.kafka.consumer.ssl.key-store-location`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.kafka.consumer.ssl.keystore-password`
  * newPropertyKey: `spring.kafka.consumer.ssl.key-store-password`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.kafka.consumer.ssl.truststore-location`
  * newPropertyKey: `spring.kafka.consumer.ssl.trust-store-location`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.kafka.consumer.ssl.truststore-password`
  * newPropertyKey: `spring.kafka.consumer.ssl.trust-store-password`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.kafka.producer.ssl.keystore-location`
  * newPropertyKey: `spring.kafka.producer.ssl.key-store-location`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.kafka.producer.ssl.keystore-password`
  * newPropertyKey: `spring.kafka.producer.ssl.key-store-password`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.kafka.producer.ssl.truststore-location`
  * newPropertyKey: `spring.kafka.producer.ssl.trust-store-location`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.kafka.producer.ssl.truststore-password`
  * newPropertyKey: `spring.kafka.producer.ssl.trust-store-password`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.kafka.ssl.keystore-location`
  * newPropertyKey: `spring.kafka.ssl.key-store-location`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.kafka.ssl.keystore-password`
  * newPropertyKey: `spring.kafka.ssl.key-store-password`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.kafka.ssl.truststore-location`
  * newPropertyKey: `spring.kafka.ssl.trust-store-location`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.kafka.ssl.truststore-password`
  * newPropertyKey: `spring.kafka.ssl.trust-store-password`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.kafka.streams.cache-max-bytes-buffering`
  * newPropertyKey: `spring.kafka.streams.cache-max-size-buffering`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.mvc.formcontent.putfilter.enabled`
  * newPropertyKey: `spring.mvc.formcontent.filter.enabled`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.rabbitmq.template.queue`
  * newPropertyKey: `spring.rabbitmq.template.default-receive-queue`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.resources.chain.gzipped`
  * newPropertyKey: `spring.resources.chain.compressed`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `management.metrics.binders.files.enabled`
  * newPropertyKey: `management.metrics.enable.process.files`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `management.metrics.binders.jvm.enabled`
  * newPropertyKey: `management.metrics.enable.jvm`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `management.metrics.binders.logback.enabled`
  * newPropertyKey: `management.metrics.enable.logback`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `management.endpoints.jmx.unique-names`
  * newPropertyKey: `spring.jmx.unique-names`

{% endtab %}

{% tab title="Yaml Recipe List" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: org.openrewrite.java.spring.boot2.SpringBootProperties_2_1
displayName: Migrate Spring Boot properties to 2.1
description: Migrate properties found in `application.properties` and `application.yml`.
tags:
  - spring
  - boot
recipeList:
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: server.jetty.max-http-post-size
      newPropertyKey: server.jetty.max-http-form-post-size
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: server.servlet.path
      newPropertyKey: spring.mvc.servlet.path
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: server.tomcat.max-http-header-size
      newPropertyKey: server.max-http-header-size
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: server.tomcat.max-http-post-size
      newPropertyKey: server.tomcat.max-http-form-post-size
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.activemq.pool.maximum-active-session-per-connection
      newPropertyKey: spring.activemq.pool.max-sessions-per-connection
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.artemis.pool.maximum-active-session-per-connection
      newPropertyKey: spring.artemis.pool.max-sessions-per-connection
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.kafka.admin.ssl.keystore-location
      newPropertyKey: spring.kafka.admin.ssl.key-store-location
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.kafka.admin.ssl.keystore-password
      newPropertyKey: spring.kafka.admin.ssl.key-store-password
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.kafka.admin.ssl.truststore-location
      newPropertyKey: spring.kafka.admin.ssl.trust-store-location
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.kafka.admin.ssl.truststore-password
      newPropertyKey: spring.kafka.admin.ssl.trust-store-password
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.kafka.consumer.ssl.keystore-location
      newPropertyKey: spring.kafka.consumer.ssl.key-store-location
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.kafka.consumer.ssl.keystore-password
      newPropertyKey: spring.kafka.consumer.ssl.key-store-password
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.kafka.consumer.ssl.truststore-location
      newPropertyKey: spring.kafka.consumer.ssl.trust-store-location
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.kafka.consumer.ssl.truststore-password
      newPropertyKey: spring.kafka.consumer.ssl.trust-store-password
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.kafka.producer.ssl.keystore-location
      newPropertyKey: spring.kafka.producer.ssl.key-store-location
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.kafka.producer.ssl.keystore-password
      newPropertyKey: spring.kafka.producer.ssl.key-store-password
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.kafka.producer.ssl.truststore-location
      newPropertyKey: spring.kafka.producer.ssl.trust-store-location
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.kafka.producer.ssl.truststore-password
      newPropertyKey: spring.kafka.producer.ssl.trust-store-password
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.kafka.ssl.keystore-location
      newPropertyKey: spring.kafka.ssl.key-store-location
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.kafka.ssl.keystore-password
      newPropertyKey: spring.kafka.ssl.key-store-password
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.kafka.ssl.truststore-location
      newPropertyKey: spring.kafka.ssl.trust-store-location
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.kafka.ssl.truststore-password
      newPropertyKey: spring.kafka.ssl.trust-store-password
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.kafka.streams.cache-max-bytes-buffering
      newPropertyKey: spring.kafka.streams.cache-max-size-buffering
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.mvc.formcontent.putfilter.enabled
      newPropertyKey: spring.mvc.formcontent.filter.enabled
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.rabbitmq.template.queue
      newPropertyKey: spring.rabbitmq.template.default-receive-queue
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.resources.chain.gzipped
      newPropertyKey: spring.resources.chain.compressed
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: management.metrics.binders.files.enabled
      newPropertyKey: management.metrics.enable.process.files
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: management.metrics.binders.jvm.enabled
      newPropertyKey: management.metrics.enable.jvm
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: management.metrics.binders.logback.enabled
      newPropertyKey: management.metrics.enable.logback
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: management.endpoints.jmx.unique-names
      newPropertyKey: spring.jmx.unique-names

```
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://app.moderne.io/recipes/org.openrewrite.java.spring.boot2.SpringBootProperties_2_1)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.

## Contributors
Tyler Van Gorder, [Knut Wannheden](mailto:knut@moderne.io), [Nick McKinney](mailto:mckinneynichoals@gmail.com), [Patrick](mailto:patway99@gmail.com), [Kyle Scully](mailto:scullykns@gmail.com)
