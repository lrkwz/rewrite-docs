# Migrate to Jakarta EE 9

**org.openrewrite.java.migrate.jakarta.JavaxMigrationToJakarta**

_Jakarta EE 9 is the first version of Jakarta EE that uses the new `jakarta` namespace._

### Tags

* jaxb
* jaxws
* jakarta

## Recipe source

[GitHub](https://github.com/openrewrite/rewrite-migrate-java/blob/main/src/main/resources/META-INF/rewrite/jakarta-ee-9.yml), [Issue Tracker](https://github.com/openrewrite/rewrite-migrate-java/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite.recipe/rewrite-migrate-java/2.5.0/jar)

* groupId: org.openrewrite.recipe
* artifactId: rewrite-migrate-java
* version: 2.5.0

{% hint style="info" %}
This recipe is composed of more than one recipe. If you want to customize the set of recipes this is composed of, you can find and copy the GitHub source for the recipe from the link above.
{% endhint %}

## Usage

This recipe has no required configuration options. It can be activated by adding a dependency on `org.openrewrite.recipe:rewrite-migrate-java:2.5.0` in your build file or by running a shell command (in which case no build changes are needed): 
{% tabs %}
{% tab title="Gradle" %}
1. Add the following to your `build.gradle` file:
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("6.6.2")
}

rewrite {
    activeRecipe("org.openrewrite.java.migrate.jakarta.JavaxMigrationToJakarta")
}

repositories {
    mavenCentral()
}

dependencies {
    rewrite("org.openrewrite.recipe:rewrite-migrate-java:2.5.0")
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
        rewrite("org.openrewrite.recipe:rewrite-migrate-java:2.5.0")
    }
    rewrite {
        activeRecipe("org.openrewrite.java.migrate.jakarta.JavaxMigrationToJakarta")
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
            <recipe>org.openrewrite.java.migrate.jakarta.JavaxMigrationToJakarta</recipe>
          </activeRecipes>
        </configuration>
        <dependencies>
          <dependency>
            <groupId>org.openrewrite.recipe</groupId>
            <artifactId>rewrite-migrate-java</artifactId>
            <version>2.5.0</version>
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
mvn -U org.openrewrite.maven:rewrite-maven-plugin:run -Drewrite.recipeArtifactCoordinates=org.openrewrite.recipe:rewrite-migrate-java:RELEASE -Drewrite.activeRecipes=org.openrewrite.java.migrate.jakarta.JavaxMigrationToJakarta
```
{% endcode %}
{% endtab %}
{% tab title="Moderne CLI" %}
You will need to have configured the [Moderne CLI](https://docs.moderne.io/moderne-cli/cli-intro) on your machine before you can run the following command.

{% code title="shell" %}
```shell
mod run . --recipe JavaxMigrationToJakarta
```
{% endcode %}
{% endtab %}
{% endtabs %}

## Definition

{% tabs %}
{% tab title="Recipe List" %}
* [Migrate deprecated `javax.activation` packages to `jakarta.activation`](../../../java/migrate/jakarta/javaxactivationmigrationtojakartaactivation.md)
* [Migrate deprecated `javax.annotation` to `jakarta.annotation`](../../../java/migrate/jakarta/javaxannotationmigrationtojakartaannotation.md)
* [Migrate deprecated `javax.security.auth.message` packages to `jakarta.security.auth.message`](../../../java/migrate/jakarta/javaxauthenticationmigrationtojakartaauthentication.md)
* [Migrate deprecated `javax.security.jacc` packages to `jakarta.security.jacc`](../../../java/migrate/jakarta/javaxauthorizationmigrationtojakartaauthorization.md)
* [Migrate deprecated `javax.batch` packages to `jakarta.batch`](../../../java/migrate/jakarta/javaxbatchmigrationtojakartabatch.md)
* [Migrate deprecated `javax.decorator` packages to `jakarta.decorator`](../../../java/migrate/jakarta/javaxdecoratortojakartadecorator.md)
* [Migrate deprecated `javax.ejb` packages to `jakarta.ejb`](../../../java/migrate/jakarta/javaxejbtojakartaejb.md)
* [Migrate deprecated `javax.el` packages to `jakarta.el`](../../../java/migrate/jakarta/javaxeltojakartael.md)
* [Migrate deprecated `javax.enterprise` packages to `jakarta.enterprise`](../../../java/migrate/jakarta/javaxenterprisetojakartaenterprise.md)
* [Migrate deprecated `javax.faces` packages to `jakarta.faces`](../../../java/migrate/jakarta/javaxfacestojakartafaces.md)
* [Migrate deprecated `javax.inject` packages to `jakarta.inject`](../../../java/migrate/jakarta/javaxinjectmigrationtojakartainject.md)
* [Migrate deprecated `javax.interceptor` packages to `jakarta.interceptor`](../../../java/migrate/jakarta/javaxinterceptortojakartainterceptor.md)
* [Migrate deprecated `javax.jms` packages to `jakarta.jms`](../../../java/migrate/jakarta/javaxjmstojakartajms.md)
* [Migrate deprecated `javax.json` packages to `jakarta.json`](../../../java/migrate/jakarta/javaxjsontojakartajson.md)
* [Migrate deprecated `javax.jws` packages to `jakarta.jws`](../../../java/migrate/jakarta/javaxjwstojakartajws.md)
* [Migrate deprecated `javax.mail` packages to `jakarta.mail`](../../../java/migrate/jakarta/javaxmailtojakartamail.md)
* [Migrate deprecated `javax.persistence` packages to `jakarta.persistence`](../../../java/migrate/jakarta/javaxpersistencetojakartapersistence.md)
* [Migrate xmlns entries in `persistence.xml` files](../../../java/migrate/jakarta/javaxpersistencexmltojakartapersistencexml.md)
* [Migrate deprecated `javax.resource` packages to `jakarta.resource`](../../../java/migrate/jakarta/javaxresourcetojakartaresource.md)
* [Migrate deprecated `javax.security.enterprise` packages to `jakarta.security.enterprise`](../../../java/migrate/jakarta/javaxsecuritytojakartasecurity.md)
* [Migrate deprecated `javax.servlet` packages to `jakarta.servlet`](../../../java/migrate/jakarta/javaxservlettojakartaservlet.md)
* [Migrate deprecated `javax.transaction` packages to `jakarta.transaction`](../../../java/migrate/jakarta/javaxtransactionmigrationtojakartatransaction.md)
* [Migrate deprecated `javax.validation` packages to `jakarta.validation`](../../../java/migrate/jakarta/javaxvalidationmigrationtojakartavalidation.md)
* [Migrate deprecated `javax.websocket` packages to `jakarta.websocket`](../../../java/migrate/jakarta/javaxwebsockettojakartawebsocket.md)
* [Migrate deprecated `javax.ws` packages to `jakarta.ws`](../../../java/migrate/jakarta/javaxwstojakartaws.md)
* [Migrate deprecated `javax.xml.bind` packages to `jakarta.xml.bind`](../../../java/migrate/jakarta/javaxxmlbindmigrationtojakartaxmlbind.md)
* [Migrate deprecated `javax.soap` packages to `jakarta.soap`](../../../java/migrate/jakarta/javaxxmlsoaptojakartaxmlsoap.md)
* [Migrate deprecated `javax.xml.ws` packages to `jakarta.xml.ws`](../../../java/migrate/jakarta/javaxxmlwsmigrationtojakartaxmlws.md)
* [Migrate Jackson from javax to jakarta namespace](../../../java/migrate/jakarta/jacksonjavaxtojakarta.md)
* [Migrate Ehcache from javax to jakarta namespace](../../../java/migrate/jakarta/ehcachejavaxtojakarta.md)
* [Migrate Johnzon from javax to jakarta namespace](../../../java/migrate/jakarta/johnzonjavaxtojakarta.md)
* [Migrate RestAssured from javax to jakarta namespace by upgrading to a version compatible with J2EE9](../../../java/migrate/jakarta/restassuredjavaxtojakarta.md)
* [Remove trailing slash from `jakarta.ws.rs.ApplicationPath` values](../../../java/migrate/jakarta/applicationpathwildcardnolongeraccepted.md)
* [Migrate `org.apache.ws.security` and `org.apache.ws.security.components.crypto` packages to  `org.apache.wss4j.common.ext` and `org.apache.wss4j.common.crypto` packages](../../../java/migrate/jakarta/updateapachewssecuritypackages.md)
* [Migrate to JavaEE8](../../../java/migrate/javaee8.md)

{% endtab %}

{% tab title="Yaml Recipe List" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: org.openrewrite.java.migrate.jakarta.JavaxMigrationToJakarta
displayName: Migrate to Jakarta EE 9
description: Jakarta EE 9 is the first version of Jakarta EE that uses the new `jakarta` namespace.
tags:
  - jaxb
  - jaxws
  - jakarta
recipeList:
  - org.openrewrite.java.migrate.jakarta.JavaxActivationMigrationToJakartaActivation
  - org.openrewrite.java.migrate.jakarta.JavaxAnnotationMigrationToJakartaAnnotation
  - org.openrewrite.java.migrate.jakarta.JavaxAuthenticationMigrationToJakartaAuthentication
  - org.openrewrite.java.migrate.jakarta.JavaxAuthorizationMigrationToJakartaAuthorization
  - org.openrewrite.java.migrate.jakarta.JavaxBatchMigrationToJakartaBatch
  - org.openrewrite.java.migrate.jakarta.JavaxDecoratorToJakartaDecorator
  - org.openrewrite.java.migrate.jakarta.JavaxEjbToJakartaEjb
  - org.openrewrite.java.migrate.jakarta.JavaxElToJakartaEl
  - org.openrewrite.java.migrate.jakarta.JavaxEnterpriseToJakartaEnterprise
  - org.openrewrite.java.migrate.jakarta.JavaxFacesToJakartaFaces
  - org.openrewrite.java.migrate.jakarta.JavaxInjectMigrationToJakartaInject
  - org.openrewrite.java.migrate.jakarta.JavaxInterceptorToJakartaInterceptor
  - org.openrewrite.java.migrate.jakarta.JavaxJmsToJakartaJms
  - org.openrewrite.java.migrate.jakarta.JavaxJsonToJakartaJson
  - org.openrewrite.java.migrate.jakarta.JavaxJwsToJakartaJws
  - org.openrewrite.java.migrate.jakarta.JavaxMailToJakartaMail
  - org.openrewrite.java.migrate.jakarta.JavaxPersistenceToJakartaPersistence
  - org.openrewrite.java.migrate.jakarta.JavaxPersistenceXmlToJakartaPersistenceXml
  - org.openrewrite.java.migrate.jakarta.JavaxResourceToJakartaResource
  - org.openrewrite.java.migrate.jakarta.JavaxSecurityToJakartaSecurity
  - org.openrewrite.java.migrate.jakarta.JavaxServletToJakartaServlet
  - org.openrewrite.java.migrate.jakarta.JavaxTransactionMigrationToJakartaTransaction
  - org.openrewrite.java.migrate.jakarta.JavaxValidationMigrationToJakartaValidation
  - org.openrewrite.java.migrate.jakarta.JavaxWebsocketToJakartaWebsocket
  - org.openrewrite.java.migrate.jakarta.JavaxWsToJakartaWs
  - org.openrewrite.java.migrate.jakarta.JavaxXmlBindMigrationToJakartaXmlBind
  - org.openrewrite.java.migrate.jakarta.JavaxXmlSoapToJakartaXmlSoap
  - org.openrewrite.java.migrate.jakarta.JavaxXmlWsMigrationToJakartaXmlWs
  - org.openrewrite.java.migrate.jakarta.JacksonJavaxToJakarta
  - org.openrewrite.java.migrate.jakarta.EhcacheJavaxToJakarta
  - org.openrewrite.java.migrate.jakarta.JohnzonJavaxToJakarta
  - org.openrewrite.java.migrate.jakarta.RestAssuredJavaxToJakarta
  - org.openrewrite.java.migrate.jakarta.ApplicationPathWildcardNoLongerAccepted
  - org.openrewrite.java.migrate.jakarta.UpdateApacheWSSecurityPackages
  - org.openrewrite.java.migrate.javaee8

```
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://app.moderne.io/recipes/org.openrewrite.java.migrate.jakarta.JavaxMigrationToJakarta)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.

## Contributors
Chuka Obinabo, ranuradh, [Tim te Beek](mailto:timtebeek@gmail.com)
