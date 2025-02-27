# Use `WebServerFactoryCustomizer`

**org.openrewrite.java.spring.boot2.MigrateToWebServerFactoryCustomizer**

_Use `WebServerFactoryCustomizer` instead of the deprecated `EmbeddedServletContainerCustomizer` in Spring Boot 2.0 or higher. This recipe will replace look for any classes that implement `EmbeddedServletContainerCustomizer` and change the interface to `WebServerFactoryCustomizer<ConfigurableServletWebServerFactory>`. This recipe also adjusts the types used in the `customize()` method from `*EmbeddedServletContainerFactory` to their `*ServletWebServerFactory` counterparts._

## Recipe source

[GitHub](https://github.com/openrewrite/rewrite-spring/blob/main/src/main/resources/META-INF/rewrite/spring-boot-20.yml), [Issue Tracker](https://github.com/openrewrite/rewrite-spring/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite.recipe/rewrite-spring/5.1.7/jar)

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
    activeRecipe("org.openrewrite.java.spring.boot2.MigrateToWebServerFactoryCustomizer")
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
        activeRecipe("org.openrewrite.java.spring.boot2.MigrateToWebServerFactoryCustomizer")
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
            <recipe>org.openrewrite.java.spring.boot2.MigrateToWebServerFactoryCustomizer</recipe>
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
mvn -U org.openrewrite.maven:rewrite-maven-plugin:run -Drewrite.recipeArtifactCoordinates=org.openrewrite.recipe:rewrite-spring:RELEASE -Drewrite.activeRecipes=org.openrewrite.java.spring.boot2.MigrateToWebServerFactoryCustomizer
```
{% endcode %}
{% endtab %}
{% tab title="Moderne CLI" %}
You will need to have configured the [Moderne CLI](https://docs.moderne.io/moderne-cli/cli-intro) on your machine before you can run the following command.

{% code title="shell" %}
```shell
mod run . --recipe MigrateToWebServerFactoryCustomizer
```
{% endcode %}
{% endtab %}
{% endtabs %}

## Definition

{% tabs %}
{% tab title="Recipe List" %}
* [Adjust configuration classes to use the `WebServerFactoryCustomizer` interface](../../../java/spring/boot2/changeembeddedservletcontainercustomizer.md)
* [Change type](../../../java/changetype.md)
  * oldFullyQualifiedTypeName: `org.springframework.boot.context.embedded.ConfigurableEmbeddedServletContainer`
  * newFullyQualifiedTypeName: `org.springframework.boot.web.servlet.server.ConfigurableServletWebServerFactory`
* [Change type](../../../java/changetype.md)
  * oldFullyQualifiedTypeName: `org.springframework.boot.context.embedded.tomcat.TomcatEmbeddedServletContainerFactory`
  * newFullyQualifiedTypeName: `org.springframework.boot.web.embedded.tomcat.TomcatServletWebServerFactory`
* [Change type](../../../java/changetype.md)
  * oldFullyQualifiedTypeName: `org.springframework.boot.context.embedded.jetty.JettyEmbeddedServletContainerFactory`
  * newFullyQualifiedTypeName: `org.springframework.boot.web.embedded.jetty.JettyServletWebServerFactory`
* [Change type](../../../java/changetype.md)
  * oldFullyQualifiedTypeName: `org.springframework.boot.context.embedded.undertow.UnderTowEmbeddedServletContainerFactory`
  * newFullyQualifiedTypeName: `org.springframework.boot.web.embedded.undertow.UnderTowServletWebServerFactory`

{% endtab %}

{% tab title="Yaml Recipe List" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: org.openrewrite.java.spring.boot2.MigrateToWebServerFactoryCustomizer
displayName: Use `WebServerFactoryCustomizer`
description: Use `WebServerFactoryCustomizer` instead of the deprecated `EmbeddedServletContainerCustomizer` in Spring Boot 2.0 or higher. This recipe will replace look for any classes that implement `EmbeddedServletContainerCustomizer` and change the interface to `WebServerFactoryCustomizer<ConfigurableServletWebServerFactory>`. This recipe also adjusts the types used in the `customize()` method from `*EmbeddedServletContainerFactory` to their `*ServletWebServerFactory` counterparts.

recipeList:
  - org.openrewrite.java.spring.boot2.ChangeEmbeddedServletContainerCustomizer
  - org.openrewrite.java.ChangeType:
      oldFullyQualifiedTypeName: org.springframework.boot.context.embedded.ConfigurableEmbeddedServletContainer
      newFullyQualifiedTypeName: org.springframework.boot.web.servlet.server.ConfigurableServletWebServerFactory
  - org.openrewrite.java.ChangeType:
      oldFullyQualifiedTypeName: org.springframework.boot.context.embedded.tomcat.TomcatEmbeddedServletContainerFactory
      newFullyQualifiedTypeName: org.springframework.boot.web.embedded.tomcat.TomcatServletWebServerFactory
  - org.openrewrite.java.ChangeType:
      oldFullyQualifiedTypeName: org.springframework.boot.context.embedded.jetty.JettyEmbeddedServletContainerFactory
      newFullyQualifiedTypeName: org.springframework.boot.web.embedded.jetty.JettyServletWebServerFactory
  - org.openrewrite.java.ChangeType:
      oldFullyQualifiedTypeName: org.springframework.boot.context.embedded.undertow.UnderTowEmbeddedServletContainerFactory
      newFullyQualifiedTypeName: org.springframework.boot.web.embedded.undertow.UnderTowServletWebServerFactory

```
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://app.moderne.io/recipes/org.openrewrite.java.spring.boot2.MigrateToWebServerFactoryCustomizer)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.

## Contributors
Tyler Van Gorder, [Jonathan Schneider](mailto:jkschneider@gmail.com), [Knut Wannheden](mailto:knut@moderne.io), [Kun Li](mailto:kun@moderne.io)
