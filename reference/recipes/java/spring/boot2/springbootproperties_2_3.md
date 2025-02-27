# Migrate Spring Boot properties to 2.3

**org.openrewrite.java.spring.boot2.SpringBootProperties\_2\_3**

_Migrate properties found in `application.properties` and `application.yml`._

### Tags

* spring
* boot

## Recipe source

[GitHub](https://github.com/openrewrite/rewrite-spring/blob/main/src/main/resources/META-INF/rewrite/spring-boot-23-properties.yml), [Issue Tracker](https://github.com/openrewrite/rewrite-spring/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite.recipe/rewrite-spring/5.1.7/jar)

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
    activeRecipe("org.openrewrite.java.spring.boot2.SpringBootProperties_2_3")
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
        activeRecipe("org.openrewrite.java.spring.boot2.SpringBootProperties_2_3")
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
            <recipe>org.openrewrite.java.spring.boot2.SpringBootProperties_2_3</recipe>
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
mvn -U org.openrewrite.maven:rewrite-maven-plugin:run -Drewrite.recipeArtifactCoordinates=org.openrewrite.recipe:rewrite-spring:RELEASE -Drewrite.activeRecipes=org.openrewrite.java.spring.boot2.SpringBootProperties_2_3
```
{% endcode %}
{% endtab %}
{% tab title="Moderne CLI" %}
You will need to have configured the [Moderne CLI](https://docs.moderne.io/moderne-cli/cli-intro) on your machine before you can run the following command.

{% code title="shell" %}
```shell
mod run . --recipe SpringBootProperties_2_3
```
{% endcode %}
{% endtab %}
{% endtabs %}

## Definition

{% tabs %}
{% tab title="Recipe List" %}
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `server.jetty.acceptors`
  * newPropertyKey: `server.jetty.threads.acceptors`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `server.jetty.max-queue-capacity`
  * newPropertyKey: `server.jetty.threads.max-queue-capacity`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `server.jetty.max-threads`
  * newPropertyKey: `server.jetty.threads.max`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `server.jetty.min-threads`
  * newPropertyKey: `server.jetty.threads.min`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `server.jetty.selectors`
  * newPropertyKey: `server.jetty.threads.selectors`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `server.jetty.thread-idle-timeout`
  * newPropertyKey: `server.jetty.threads.idle-timeout`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `server.tomcat.host-header`
  * newPropertyKey: `server.tomcat.remoteip.host-header`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `server.tomcat.internal-proxies`
  * newPropertyKey: `server.tomcat.remoteip.internal-proxies`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `server.tomcat.max-threads`
  * newPropertyKey: `server.tomcat.threads.max`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `server.tomcat.min-spare-threads`
  * newPropertyKey: `server.tomcat.threads.min-spare`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `server.tomcat.port-header`
  * newPropertyKey: `server.tomcat.remote.port-header`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `server.tomcat.protocol-header`
  * newPropertyKey: `server.tomcat.remoteip.protocol-header`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `server.tomcat.protocol-header-https-value`
  * newPropertyKey: `server.tomcat.remoteip.protocol-header-https-value`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `server.tomcat.remote-ip-header`
  * newPropertyKey: `server.tomcat.remoteip.remote-ip-header`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `server.undertow.io-threads`
  * newPropertyKey: `server.undertow.threads.io`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `server.undertow.worker-threads`
  * newPropertyKey: `server.undertow.threads.worker`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.couchbase.bootstrap-hosts`
  * newPropertyKey: `spring.couchbase.connection-string`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.couchbase.env.endpoints.queryservice.max-endpoints`
  * newPropertyKey: `spring.couchbase.env.io.max-endpoints`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.couchbase.env.endpoints.queryservice.min-endpoints`
  * newPropertyKey: `spring.couchbase.env.io.min-endpoints`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.couchbase.env.endpoints.viewservice.max-endpoints`
  * newPropertyKey: `spring.couchbase.env.io.max-endpoints`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.couchbase.env.endpoints.viewservice.min-endpoints`
  * newPropertyKey: `spring.couchbase.env.io.min-endpoints`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.data.cassandra.cluster-name`
  * newPropertyKey: `spring.data.cassandra.session-name`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.data.cassandra.connect-timeout`
  * newPropertyKey: `spring.data.cassandra.connection.init-query-timeout`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.data.cassandra.consistency-level`
  * newPropertyKey: `spring.data.cassandra.request.consistency`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.data.cassandra.fetch-size`
  * newPropertyKey: `spring.data.cassandra.request.page-size`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.data.cassandra.pool.max-queue-size`
  * newPropertyKey: `spring.data.cassandra.request.throttler.max-queue-size`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.data.cassandra.read-timeout`
  * newPropertyKey: `spring.data.cassandra.request.timeout`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.data.cassandra.serial-consistency-level`
  * newPropertyKey: `spring.data.cassandra.request.serial-consistency`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.http.converters.preferred-json-mapper`
  * newPropertyKey: `spring.mvc.converters.preferred-json-mapper`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.http.encoding.charset`
  * newPropertyKey: `server.servlet.encoding.charset`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.http.encoding.enabled`
  * newPropertyKey: `server.servlet.encoding.enabled`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.http.encoding.force`
  * newPropertyKey: `server.servlet.encoding.force`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.http.encoding.force-request`
  * newPropertyKey: `server.servlet.encoding.force-request`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.http.encoding.force-response`
  * newPropertyKey: `server.servlet.encoding.force-response`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.http.encoding.mapping`
  * newPropertyKey: `server.servlet.encoding.mapping`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.http.log-request-details`
  * newPropertyKey: `spring.mvc.log-request-details`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.mvc.date-format`
  * newPropertyKey: `spring.mvc.format.date`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.webflux.date-format`
  * newPropertyKey: `spring.webflux.format.date`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `management.health.probes.enabled`
  * newPropertyKey: `management.endpoint.health.probes.enabled`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `management.metrics.distribution.sla`
  * newPropertyKey: `management.metrics.distribution.slo`

{% endtab %}

{% tab title="Yaml Recipe List" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: org.openrewrite.java.spring.boot2.SpringBootProperties_2_3
displayName: Migrate Spring Boot properties to 2.3
description: Migrate properties found in `application.properties` and `application.yml`.
tags:
  - spring
  - boot
recipeList:
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: server.jetty.acceptors
      newPropertyKey: server.jetty.threads.acceptors
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: server.jetty.max-queue-capacity
      newPropertyKey: server.jetty.threads.max-queue-capacity
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: server.jetty.max-threads
      newPropertyKey: server.jetty.threads.max
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: server.jetty.min-threads
      newPropertyKey: server.jetty.threads.min
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: server.jetty.selectors
      newPropertyKey: server.jetty.threads.selectors
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: server.jetty.thread-idle-timeout
      newPropertyKey: server.jetty.threads.idle-timeout
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: server.tomcat.host-header
      newPropertyKey: server.tomcat.remoteip.host-header
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: server.tomcat.internal-proxies
      newPropertyKey: server.tomcat.remoteip.internal-proxies
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: server.tomcat.max-threads
      newPropertyKey: server.tomcat.threads.max
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: server.tomcat.min-spare-threads
      newPropertyKey: server.tomcat.threads.min-spare
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: server.tomcat.port-header
      newPropertyKey: server.tomcat.remote.port-header
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: server.tomcat.protocol-header
      newPropertyKey: server.tomcat.remoteip.protocol-header
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: server.tomcat.protocol-header-https-value
      newPropertyKey: server.tomcat.remoteip.protocol-header-https-value
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: server.tomcat.remote-ip-header
      newPropertyKey: server.tomcat.remoteip.remote-ip-header
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: server.undertow.io-threads
      newPropertyKey: server.undertow.threads.io
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: server.undertow.worker-threads
      newPropertyKey: server.undertow.threads.worker
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.couchbase.bootstrap-hosts
      newPropertyKey: spring.couchbase.connection-string
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.couchbase.env.endpoints.queryservice.max-endpoints
      newPropertyKey: spring.couchbase.env.io.max-endpoints
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.couchbase.env.endpoints.queryservice.min-endpoints
      newPropertyKey: spring.couchbase.env.io.min-endpoints
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.couchbase.env.endpoints.viewservice.max-endpoints
      newPropertyKey: spring.couchbase.env.io.max-endpoints
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.couchbase.env.endpoints.viewservice.min-endpoints
      newPropertyKey: spring.couchbase.env.io.min-endpoints
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.data.cassandra.cluster-name
      newPropertyKey: spring.data.cassandra.session-name
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.data.cassandra.connect-timeout
      newPropertyKey: spring.data.cassandra.connection.init-query-timeout
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.data.cassandra.consistency-level
      newPropertyKey: spring.data.cassandra.request.consistency
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.data.cassandra.fetch-size
      newPropertyKey: spring.data.cassandra.request.page-size
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.data.cassandra.pool.max-queue-size
      newPropertyKey: spring.data.cassandra.request.throttler.max-queue-size
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.data.cassandra.read-timeout
      newPropertyKey: spring.data.cassandra.request.timeout
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.data.cassandra.serial-consistency-level
      newPropertyKey: spring.data.cassandra.request.serial-consistency
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.http.converters.preferred-json-mapper
      newPropertyKey: spring.mvc.converters.preferred-json-mapper
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.http.encoding.charset
      newPropertyKey: server.servlet.encoding.charset
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.http.encoding.enabled
      newPropertyKey: server.servlet.encoding.enabled
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.http.encoding.force
      newPropertyKey: server.servlet.encoding.force
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.http.encoding.force-request
      newPropertyKey: server.servlet.encoding.force-request
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.http.encoding.force-response
      newPropertyKey: server.servlet.encoding.force-response
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.http.encoding.mapping
      newPropertyKey: server.servlet.encoding.mapping
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.http.log-request-details
      newPropertyKey: spring.mvc.log-request-details
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.mvc.date-format
      newPropertyKey: spring.mvc.format.date
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.webflux.date-format
      newPropertyKey: spring.webflux.format.date
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: management.health.probes.enabled
      newPropertyKey: management.endpoint.health.probes.enabled
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: management.metrics.distribution.sla
      newPropertyKey: management.metrics.distribution.slo

```
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://app.moderne.io/recipes/org.openrewrite.java.spring.boot2.SpringBootProperties_2_3)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.

## Contributors
Tyler Van Gorder, [Knut Wannheden](mailto:knut@moderne.io), [Nick McKinney](mailto:mckinneynichoals@gmail.com), [Patrick](mailto:patway99@gmail.com), [Kyle Scully](mailto:scullykns@gmail.com)
