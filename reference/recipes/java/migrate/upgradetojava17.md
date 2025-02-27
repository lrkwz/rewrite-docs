# Migrate to Java 17

**org.openrewrite.java.migrate.UpgradeToJava17**

_This recipe will apply changes commonly needed when migrating to Java 17. Specifically, for those applications that are built on Java 8, this recipe will update and add dependencies on J2EE libraries that are no longer directly bundled with the JDK. This recipe will also replace deprecated API with equivalents when there is a clear migration strategy. Build files will also be updated to use Java 17 as the target/source and plugins will be also be upgraded to versions that are compatible with Java 17._

### Tags

* java17

## Recipe source

[GitHub](https://github.com/openrewrite/rewrite-migrate-java/blob/main/src/main/resources/META-INF/rewrite/java-version-17.yml), [Issue Tracker](https://github.com/openrewrite/rewrite-migrate-java/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite.recipe/rewrite-migrate-java/2.5.0/jar)

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
    activeRecipe("org.openrewrite.java.migrate.UpgradeToJava17")
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
        activeRecipe("org.openrewrite.java.migrate.UpgradeToJava17")
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
            <recipe>org.openrewrite.java.migrate.UpgradeToJava17</recipe>
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
mvn -U org.openrewrite.maven:rewrite-maven-plugin:run -Drewrite.recipeArtifactCoordinates=org.openrewrite.recipe:rewrite-migrate-java:RELEASE -Drewrite.activeRecipes=org.openrewrite.java.migrate.UpgradeToJava17
```
{% endcode %}
{% endtab %}
{% tab title="Moderne CLI" %}
You will need to have configured the [Moderne CLI](https://docs.moderne.io/moderne-cli/cli-intro) on your machine before you can run the following command.

{% code title="shell" %}
```shell
mod run . --recipe UpgradeToJava17
```
{% endcode %}
{% endtab %}
{% endtabs %}

## Definition

{% tabs %}
{% tab title="Recipe List" %}
* [Migrate to Java 11](../../java/migrate/java8tojava11.md)
* [Change Maven Java version property values to 17](../../java/migrate/javaversion17.md)
* [Prefer `String#formatted(Object...)`](../../java/migrate/lang/stringformatted.md)
* [Upgrade `actions/setup-java` `java-version`](../../github/setupjavaupgradejavaversion.md)
  * minimumJavaMajorVersion: `17`
* [Changes code to use Java 17's `instanceof` pattern matching](../../staticanalysis/instanceofpatternmatch.md)
* [Remove methods calls](../../java/migrate/removemethodinvocation.md)
  * methodPattern: `java.lang.Runtime traceInstructions(boolean)`
* [Remove methods calls](../../java/migrate/removemethodinvocation.md)
  * methodPattern: `java.lang.System traceMethodCalls(boolean)`
* [Use text blocks](../../java/migrate/lang/usetextblocks.md)
  * convertStringsWithoutNewlines: `true`
* [Use `java.security.cert` instead of `javax.security.cert`](../../java/migrate/deprecatedjavaxsecuritycert.md)
* [Adopt `setLongThreadID` in `java.util.logging.LogRecord`](../../java/migrate/deprecatedlogrecordthreadid.md)
* [Use `SunJSSE` instead of `com.sun.net.ssl.internal.ssl.Provider`](../../java/migrate/removedlegacysunjsseprovidername.md)
* [Set visibility of `premain` and `agentmain` methods to `public`](../../java/migrate/jre17agentmainpremainpublic.md)
* [Upgrade Maven plugin version](../../maven/upgradepluginversion.md)
  * groupId: `org.apache.maven.plugins`
  * artifactId: `maven-checkstyle-plugin`
  * newVersion: `3.x`

{% endtab %}

{% tab title="Yaml Recipe List" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: org.openrewrite.java.migrate.UpgradeToJava17
displayName: Migrate to Java 17
description: This recipe will apply changes commonly needed when migrating to Java 17. Specifically, for those applications that are built on Java 8, this recipe will update and add dependencies on J2EE libraries that are no longer directly bundled with the JDK. This recipe will also replace deprecated API with equivalents when there is a clear migration strategy. Build files will also be updated to use Java 17 as the target/source and plugins will be also be upgraded to versions that are compatible with Java 17.

tags:
  - java17
recipeList:
  - org.openrewrite.java.migrate.Java8toJava11
  - org.openrewrite.java.migrate.JavaVersion17
  - org.openrewrite.java.migrate.lang.StringFormatted
  - org.openrewrite.github.SetupJavaUpgradeJavaVersion:
      minimumJavaMajorVersion: 17
  - org.openrewrite.staticanalysis.InstanceOfPatternMatch
  - org.openrewrite.java.migrate.RemoveMethodInvocation:
      methodPattern: java.lang.Runtime traceInstructions(boolean)
  - org.openrewrite.java.migrate.RemoveMethodInvocation:
      methodPattern: java.lang.System traceMethodCalls(boolean)
  - org.openrewrite.java.migrate.lang.UseTextBlocks:
      convertStringsWithoutNewlines: true
  - org.openrewrite.java.migrate.DeprecatedJavaxSecurityCert
  - org.openrewrite.java.migrate.DeprecatedLogRecordThreadID
  - org.openrewrite.java.migrate.RemovedLegacySunJSSEProviderName
  - org.openrewrite.java.migrate.Jre17AgentMainPreMainPublic
  - org.openrewrite.maven.UpgradePluginVersion:
      groupId: org.apache.maven.plugins
      artifactId: maven-checkstyle-plugin
      newVersion: 3.x

```
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://app.moderne.io/recipes/org.openrewrite.java.migrate.UpgradeToJava17)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.

## Contributors
Chuka Obinabo, [Sam Snyder](mailto:sam@moderne.io), [Shannon Pamperl](mailto:shanman190@gmail.com), [Tim te Beek](mailto:tim.te.beek@jdriven.com), [Satvika Eda](mailto:satvika164.reddy@gmail.com), Tyler Van Gorder, [Nick McKinney](mailto:mckinneynicholas@gmail.com), [traceyyoshima](mailto:tracey.yoshima@gmail.com), [Knut Wannheden](mailto:knut@moderne.io), [Jonathan Schneider](mailto:jkschneider@gmail.com), Adam Slaski, [Yifeng Jin](mailto:yifeng.jyf@alibaba-inc.com), Aaron Gershman, [Patrick](mailto:patway99@gmail.com), Kun Li, [Aaron Gershman](mailto:aegershman@gmail.com), [Tim te Beek](mailto:timtebeek@gmail.com), [Jonathan Schnéider](mailto:jkschneider@gmail.com), [Tim te Beek](mailto:tim@moderne.io), [Kun Li](mailto:kun@moderne.io), [Joan Viladrosa](mailto:joan@moderne.io), Aakarshit Uppal, [Tracey Yoshima](mailto:tracey.yoshima@gmail.com), Josh Soref, [Simon Verhoeven](mailto:verhoeven.simon@gmail.com)
