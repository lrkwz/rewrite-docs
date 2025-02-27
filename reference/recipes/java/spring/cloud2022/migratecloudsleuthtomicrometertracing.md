# Migrate Spring Cloud Sleuth 3.1 to Micrometer Tracing 1.0

**org.openrewrite.java.spring.cloud2022.MigrateCloudSleuthToMicrometerTracing**

_Spring Cloud Sleuth has been discontinued and only compatible with Spring Boot 2.x._

### Tags

* spring
* cloud
* tracing
* sleuth
* micrometer

## Recipe source

[GitHub](https://github.com/openrewrite/rewrite-spring/blob/main/src/main/resources/META-INF/rewrite/spring-cloud-2022.yml), [Issue Tracker](https://github.com/openrewrite/rewrite-spring/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite.recipe/rewrite-spring/5.1.7/jar)

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
    activeRecipe("org.openrewrite.java.spring.cloud2022.MigrateCloudSleuthToMicrometerTracing")
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
        activeRecipe("org.openrewrite.java.spring.cloud2022.MigrateCloudSleuthToMicrometerTracing")
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
            <recipe>org.openrewrite.java.spring.cloud2022.MigrateCloudSleuthToMicrometerTracing</recipe>
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
mvn -U org.openrewrite.maven:rewrite-maven-plugin:run -Drewrite.recipeArtifactCoordinates=org.openrewrite.recipe:rewrite-spring:RELEASE -Drewrite.activeRecipes=org.openrewrite.java.spring.cloud2022.MigrateCloudSleuthToMicrometerTracing
```
{% endcode %}
{% endtab %}
{% tab title="Moderne CLI" %}
You will need to have configured the [Moderne CLI](https://docs.moderne.io/moderne-cli/cli-intro) on your machine before you can run the following command.

{% code title="shell" %}
```shell
mod run . --recipe MigrateCloudSleuthToMicrometerTracing
```
{% endcode %}
{% endtab %}
{% endtabs %}

## Definition

{% tabs %}
{% tab title="Recipe List" %}
* [Add logging.pattern.level for traceId and spanId](../../../java/spring/cloud2022/addloggingpatternlevelforsleuth.md)
* [Change Maven dependency groupId, artifactId and/or the version](../../../maven/changedependencygroupidandartifactid.md)
  * oldGroupId: `org.springframework.cloud`
  * oldArtifactId: `spring-cloud-starter-sleuth`
  * newGroupId: `io.micrometer`
  * newArtifactId: `micrometer-tracing-bridge-brave`
  * newVersion: `1.0.x`
* [Change Maven dependency groupId, artifactId and/or the version](../../../maven/changedependencygroupidandartifactid.md)
  * oldGroupId: `org.springframework.cloud`
  * oldArtifactId: `spring-cloud-sleuth-otel-dependencies`
  * newGroupId: `io.micrometer`
  * newArtifactId: `micrometer-tracing-bridge-otel`
  * newVersion: `1.0.x`
* [Change Maven dependency groupId, artifactId and/or the version](../../../maven/changedependencygroupidandartifactid.md)
  * oldGroupId: `org.springframework.cloud`
  * oldArtifactId: `spring-cloud-sleuth-api`
  * newGroupId: `io.micrometer`
  * newArtifactId: `micrometer-tracing`
  * newVersion: `1.0.x`
* [Change Maven dependency groupId, artifactId and/or the version](../../../maven/changedependencygroupidandartifactid.md)
  * oldGroupId: `org.springframework.cloud`
  * oldArtifactId: `spring-cloud-sleuth-autoconfigure`
  * newGroupId: `org.springframework.boot`
  * newArtifactId: `spring-boot-actuator-autoconfigure`
* [Change Maven dependency groupId, artifactId and/or the version](../../../maven/changedependencygroupidandartifactid.md)
  * oldGroupId: `org.springframework.cloud`
  * oldArtifactId: `spring-cloud-sleuth-otel-autoconfigure`
  * newGroupId: `org.springframework.boot`
  * newArtifactId: `spring-boot-actuator-autoconfigure`
* [Change Maven dependency groupId, artifactId and/or the version](../../../maven/changedependencygroupidandartifactid.md)
  * oldGroupId: `org.springframework.cloud`
  * oldArtifactId: `spring-cloud-sleuth-zipkin`
  * newGroupId: `io.zipkin.reporter2`
  * newArtifactId: `zipkin-reporter-brave`
  * newVersion: `2.16.x`
* [Add Gradle or Maven dependency](../../../java/dependencies/adddependency.md)
  * groupId: `org.springframework.boot`
  * artifactId: `spring-boot-starter-actuator`
  * version: `3.0.x`
  * onlyIfUsing: `org.springframework.cloud.sleuth..*`
  * acceptTransitive: `true`
* [Add Gradle or Maven dependency](../../../java/dependencies/adddependency.md)
  * groupId: `io.micrometer`
  * artifactId: `micrometer-tracing`
  * version: `1.0.x`
  * onlyIfUsing: `org.springframework.cloud.sleuth.annotation.*`
  * acceptTransitive: `true`
* [Add Gradle or Maven dependency](../../../java/dependencies/adddependency.md)
  * groupId: `org.springframework.boot`
  * artifactId: `spring-boot-starter-aop`
  * version: `3.0.x`
  * onlyIfUsing: `org.springframework.cloud.sleuth.annotation.*`
  * acceptTransitive: `true`
* [Remove a Gradle or Maven dependency](../../../java/dependencies/removedependency.md)
  * groupId: `org.springframework.cloud`
  * artifactId: `spring-cloud-sleuth-*`
* [Remove Maven managed dependency](../../../maven/removemanageddependency.md)
  * groupId: `org.springframework.cloud`
  * artifactId: `spring-cloud-sleuth-*`
* [Remove redundant explicit dependency versions](../../../maven/removeredundantdependencyversions.md)
  * groupPattern: `io.micrometer`
  * artifactPattern: `micrometer-tracing*`
  * onlyIfVersionsMatch: `false`
* [Change type](../../../java/changetype.md)
  * oldFullyQualifiedTypeName: `org.springframework.cloud.sleuth.exporter.SpanFilter`
  * newFullyQualifiedTypeName: `io.micrometer.tracing.exporter.SpanExportingPredicate`
* [Change type](../../../java/changetype.md)
  * oldFullyQualifiedTypeName: `org.springframework.cloud.sleuth.exporter.SpanIgnoringSpanFilter`
  * newFullyQualifiedTypeName: `io.micrometer.tracing.exporter.SpanIgnoringSpanExportingPredicate`
* [Rename package name](../../../java/changepackage.md)
  * oldPackageName: `org.springframework.cloud.sleuth.autoconfig`
  * newPackageName: `org.springframework.boot.actuate.autoconfigure.tracing`
  * recursive: `true`
* [Rename package name](../../../java/changepackage.md)
  * oldPackageName: `org.springframework.cloud.sleuth`
  * newPackageName: `io.micrometer.tracing`
  * recursive: `true`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.sleuth.enabled`
  * newPropertyKey: `management.tracing.enabled`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.sleuth.batch.enabled`
  * newPropertyKey: `management.tracing.enabled`
* [Delete a spring configuration property](../../../java/spring/deletespringproperty.md)
  * propertyKey: `spring.sleuth.supports-join`
* [Delete a spring configuration property](../../../java/spring/deletespringproperty.md)
  * propertyKey: `spring.sleuth.trace-id128`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.sleuth.propagation.type`
  * newPropertyKey: `management.tracing.propagation.type`
* [Delete a spring configuration property](../../../java/spring/deletespringproperty.md)
  * propertyKey: `spring.sleuth.sampler.rate`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.sleuth.sampler.probability`
  * newPropertyKey: `management.tracing.sampling.probability`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.sleuth.baggage.remote-fields`
  * newPropertyKey: `management.tracing.baggage.remote-fields`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.sleuth.propagation-keys`
  * newPropertyKey: `management.tracing.baggage.remote-fields`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.sleuth.baggage.correlation-enabled`
  * newPropertyKey: `management.tracing.baggage.correlation.enabled`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.sleuth.baggage.correlation-fields`
  * newPropertyKey: `management.tracing.baggage.correlation.fields`

{% endtab %}

{% tab title="Yaml Recipe List" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: org.openrewrite.java.spring.cloud2022.MigrateCloudSleuthToMicrometerTracing
displayName: Migrate Spring Cloud Sleuth 3.1 to Micrometer Tracing 1.0
description: Spring Cloud Sleuth has been discontinued and only compatible with Spring Boot 2.x.
tags:
  - spring
  - cloud
  - tracing
  - sleuth
  - micrometer
recipeList:
  - org.openrewrite.java.spring.cloud2022.AddLoggingPatternLevelForSleuth
  - org.openrewrite.maven.ChangeDependencyGroupIdAndArtifactId:
      oldGroupId: org.springframework.cloud
      oldArtifactId: spring-cloud-starter-sleuth
      newGroupId: io.micrometer
      newArtifactId: micrometer-tracing-bridge-brave
      newVersion: 1.0.x
  - org.openrewrite.maven.ChangeDependencyGroupIdAndArtifactId:
      oldGroupId: org.springframework.cloud
      oldArtifactId: spring-cloud-sleuth-otel-dependencies
      newGroupId: io.micrometer
      newArtifactId: micrometer-tracing-bridge-otel
      newVersion: 1.0.x
  - org.openrewrite.maven.ChangeDependencyGroupIdAndArtifactId:
      oldGroupId: org.springframework.cloud
      oldArtifactId: spring-cloud-sleuth-api
      newGroupId: io.micrometer
      newArtifactId: micrometer-tracing
      newVersion: 1.0.x
  - org.openrewrite.maven.ChangeDependencyGroupIdAndArtifactId:
      oldGroupId: org.springframework.cloud
      oldArtifactId: spring-cloud-sleuth-autoconfigure
      newGroupId: org.springframework.boot
      newArtifactId: spring-boot-actuator-autoconfigure
  - org.openrewrite.maven.ChangeDependencyGroupIdAndArtifactId:
      oldGroupId: org.springframework.cloud
      oldArtifactId: spring-cloud-sleuth-otel-autoconfigure
      newGroupId: org.springframework.boot
      newArtifactId: spring-boot-actuator-autoconfigure
  - org.openrewrite.maven.ChangeDependencyGroupIdAndArtifactId:
      oldGroupId: org.springframework.cloud
      oldArtifactId: spring-cloud-sleuth-zipkin
      newGroupId: io.zipkin.reporter2
      newArtifactId: zipkin-reporter-brave
      newVersion: 2.16.x
  - org.openrewrite.java.dependencies.AddDependency:
      groupId: org.springframework.boot
      artifactId: spring-boot-starter-actuator
      version: 3.0.x
      onlyIfUsing: org.springframework.cloud.sleuth..*
      acceptTransitive: true
  - org.openrewrite.java.dependencies.AddDependency:
      groupId: io.micrometer
      artifactId: micrometer-tracing
      version: 1.0.x
      onlyIfUsing: org.springframework.cloud.sleuth.annotation.*
      acceptTransitive: true
  - org.openrewrite.java.dependencies.AddDependency:
      groupId: org.springframework.boot
      artifactId: spring-boot-starter-aop
      version: 3.0.x
      onlyIfUsing: org.springframework.cloud.sleuth.annotation.*
      acceptTransitive: true
  - org.openrewrite.java.dependencies.RemoveDependency:
      groupId: org.springframework.cloud
      artifactId: spring-cloud-sleuth-*
  - org.openrewrite.maven.RemoveManagedDependency:
      groupId: org.springframework.cloud
      artifactId: spring-cloud-sleuth-*
  - org.openrewrite.maven.RemoveRedundantDependencyVersions:
      groupPattern: io.micrometer
      artifactPattern: micrometer-tracing*
      onlyIfVersionsMatch: false
  - org.openrewrite.java.ChangeType:
      oldFullyQualifiedTypeName: org.springframework.cloud.sleuth.exporter.SpanFilter
      newFullyQualifiedTypeName: io.micrometer.tracing.exporter.SpanExportingPredicate
  - org.openrewrite.java.ChangeType:
      oldFullyQualifiedTypeName: org.springframework.cloud.sleuth.exporter.SpanIgnoringSpanFilter
      newFullyQualifiedTypeName: io.micrometer.tracing.exporter.SpanIgnoringSpanExportingPredicate
  - org.openrewrite.java.ChangePackage:
      oldPackageName: org.springframework.cloud.sleuth.autoconfig
      newPackageName: org.springframework.boot.actuate.autoconfigure.tracing
      recursive: true
  - org.openrewrite.java.ChangePackage:
      oldPackageName: org.springframework.cloud.sleuth
      newPackageName: io.micrometer.tracing
      recursive: true
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.sleuth.enabled
      newPropertyKey: management.tracing.enabled
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.sleuth.batch.enabled
      newPropertyKey: management.tracing.enabled
  - org.openrewrite.java.spring.DeleteSpringProperty:
      propertyKey: spring.sleuth.supports-join
  - org.openrewrite.java.spring.DeleteSpringProperty:
      propertyKey: spring.sleuth.trace-id128
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.sleuth.propagation.type
      newPropertyKey: management.tracing.propagation.type
  - org.openrewrite.java.spring.DeleteSpringProperty:
      propertyKey: spring.sleuth.sampler.rate
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.sleuth.sampler.probability
      newPropertyKey: management.tracing.sampling.probability
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.sleuth.baggage.remote-fields
      newPropertyKey: management.tracing.baggage.remote-fields
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.sleuth.propagation-keys
      newPropertyKey: management.tracing.baggage.remote-fields
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.sleuth.baggage.correlation-enabled
      newPropertyKey: management.tracing.baggage.correlation.enabled
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.sleuth.baggage.correlation-fields
      newPropertyKey: management.tracing.baggage.correlation.fields

```
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://app.moderne.io/recipes/org.openrewrite.java.spring.cloud2022.MigrateCloudSleuthToMicrometerTracing)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.

## Contributors
Tyler Van Gorder, [Knut Wannheden](mailto:knut@moderne.io), [Nick McKinney](mailto:mckinneynichoals@gmail.com), [Patrick](mailto:patway99@gmail.com), Kun Li, [Kyle Scully](mailto:scullykns@gmail.com)
