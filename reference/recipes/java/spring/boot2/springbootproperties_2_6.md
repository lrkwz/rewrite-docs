# Migrate Spring Boot properties to 2.6

**org.openrewrite.java.spring.boot2.SpringBootProperties\_2\_6**

_Migrate properties found in `application.properties` and `application.yml`._

### Tags

* spring
* boot

## Recipe source

[GitHub](https://github.com/openrewrite/rewrite-spring/blob/main/src/main/resources/META-INF/rewrite/spring-boot-26-properties.yml), [Issue Tracker](https://github.com/openrewrite/rewrite-spring/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite.recipe/rewrite-spring/5.1.7/jar)

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
    activeRecipe("org.openrewrite.java.spring.boot2.SpringBootProperties_2_6")
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
        activeRecipe("org.openrewrite.java.spring.boot2.SpringBootProperties_2_6")
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
            <recipe>org.openrewrite.java.spring.boot2.SpringBootProperties_2_6</recipe>
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
mvn -U org.openrewrite.maven:rewrite-maven-plugin:run -Drewrite.recipeArtifactCoordinates=org.openrewrite.recipe:rewrite-spring:RELEASE -Drewrite.activeRecipes=org.openrewrite.java.spring.boot2.SpringBootProperties_2_6
```
{% endcode %}
{% endtab %}
{% tab title="Moderne CLI" %}
You will need to have configured the [Moderne CLI](https://docs.moderne.io/moderne-cli/cli-intro) on your machine before you can run the following command.

{% code title="shell" %}
```shell
mod run . --recipe SpringBootProperties_2_6
```
{% endcode %}
{% endtab %}
{% endtabs %}

## Definition

{% tabs %}
{% tab title="Recipe List" %}
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `management.metrics.export.dynatrace.device-id`
  * newPropertyKey: `management.metrics.export.dynatrace.v1.device-id`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `management.metrics.export.dynatrace.group`
  * newPropertyKey: `management.metrics.export.dynatrace.v1.group`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `management.metrics.export.dynatrace.technology-type`
  * newPropertyKey: `management.metrics.export.dynatrace.v1.technology-type`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.data.elasticsearch.client.reactive.connection-timeout`
  * newPropertyKey: `spring.elasticsearch.connection-timeout`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.data.elasticsearch.client.reactive.endpoints`
  * newPropertyKey: `spring.elasticsearch.uris`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.data.elasticsearch.client.reactive.max-in-memory-size`
  * newPropertyKey: `spring.elasticsearch.webclient.max-in-memory-size`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.data.elasticsearch.client.reactive.password`
  * newPropertyKey: `spring.elasticsearch.password`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.data.elasticsearch.client.reactive.socket-timeout`
  * newPropertyKey: `spring.elasticsearch.socket-timeout`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.data.elasticsearch.client.reactive.username`
  * newPropertyKey: `spring.elasticsearch.username`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.elasticsearch.rest.connection-timeout`
  * newPropertyKey: `spring.elasticsearch.connection-timeout`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.elasticsearch.rest.password`
  * newPropertyKey: `spring.elasticsearch.password`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.elasticsearch.rest.read-timeout`
  * newPropertyKey: `spring.elasticsearch.socket-timeout`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.elasticsearch.rest.sniffer.delay-after-failure`
  * newPropertyKey: `spring.elasticsearch.restclient.sniffer.delay-after-failure`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.elasticsearch.rest.sniffer.interval`
  * newPropertyKey: `spring.elasticsearch.restclient.sniffer.interval`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.elasticsearch.rest.uris`
  * newPropertyKey: `spring.elasticsearch.uris`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.elasticsearch.rest.username`
  * newPropertyKey: `spring.elasticsearch.username`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.flyway.ignore-future-migrations`
  * newPropertyKey: `spring.flyway.ignore-migration-patterns`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.flyway.ignore-ignored-migrations`
  * newPropertyKey: `spring.flyway.ignore-migration-patterns`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.flyway.ignore-missing-migrations`
  * newPropertyKey: `spring.flyway.ignore-migration-patterns`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.flyway.ignore-pending-migrations`
  * newPropertyKey: `spring.flyway.ignore-migration-patterns`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.flyway.oracle-kerberos-config-file`
  * newPropertyKey: `spring.flyway.kerberos-config-file`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.webflux.session.cookie.same-site`
  * newPropertyKey: `server.reactive.session.cookie.same-site`

{% endtab %}

{% tab title="Yaml Recipe List" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: org.openrewrite.java.spring.boot2.SpringBootProperties_2_6
displayName: Migrate Spring Boot properties to 2.6
description: Migrate properties found in `application.properties` and `application.yml`.
tags:
  - spring
  - boot
recipeList:
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: management.metrics.export.dynatrace.device-id
      newPropertyKey: management.metrics.export.dynatrace.v1.device-id
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: management.metrics.export.dynatrace.group
      newPropertyKey: management.metrics.export.dynatrace.v1.group
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: management.metrics.export.dynatrace.technology-type
      newPropertyKey: management.metrics.export.dynatrace.v1.technology-type
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.data.elasticsearch.client.reactive.connection-timeout
      newPropertyKey: spring.elasticsearch.connection-timeout
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.data.elasticsearch.client.reactive.endpoints
      newPropertyKey: spring.elasticsearch.uris
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.data.elasticsearch.client.reactive.max-in-memory-size
      newPropertyKey: spring.elasticsearch.webclient.max-in-memory-size
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.data.elasticsearch.client.reactive.password
      newPropertyKey: spring.elasticsearch.password
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.data.elasticsearch.client.reactive.socket-timeout
      newPropertyKey: spring.elasticsearch.socket-timeout
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.data.elasticsearch.client.reactive.username
      newPropertyKey: spring.elasticsearch.username
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.elasticsearch.rest.connection-timeout
      newPropertyKey: spring.elasticsearch.connection-timeout
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.elasticsearch.rest.password
      newPropertyKey: spring.elasticsearch.password
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.elasticsearch.rest.read-timeout
      newPropertyKey: spring.elasticsearch.socket-timeout
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.elasticsearch.rest.sniffer.delay-after-failure
      newPropertyKey: spring.elasticsearch.restclient.sniffer.delay-after-failure
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.elasticsearch.rest.sniffer.interval
      newPropertyKey: spring.elasticsearch.restclient.sniffer.interval
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.elasticsearch.rest.uris
      newPropertyKey: spring.elasticsearch.uris
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.elasticsearch.rest.username
      newPropertyKey: spring.elasticsearch.username
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.flyway.ignore-future-migrations
      newPropertyKey: spring.flyway.ignore-migration-patterns
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.flyway.ignore-ignored-migrations
      newPropertyKey: spring.flyway.ignore-migration-patterns
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.flyway.ignore-missing-migrations
      newPropertyKey: spring.flyway.ignore-migration-patterns
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.flyway.ignore-pending-migrations
      newPropertyKey: spring.flyway.ignore-migration-patterns
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.flyway.oracle-kerberos-config-file
      newPropertyKey: spring.flyway.kerberos-config-file
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.webflux.session.cookie.same-site
      newPropertyKey: server.reactive.session.cookie.same-site

```
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://app.moderne.io/recipes/org.openrewrite.java.spring.boot2.SpringBootProperties_2_6)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.

## Contributors
Tyler Van Gorder, [Knut Wannheden](mailto:knut@moderne.io), [Nick McKinney](mailto:mckinneynichoals@gmail.com), [Patrick](mailto:patway99@gmail.com), [Kyle Scully](mailto:scullykns@gmail.com)
