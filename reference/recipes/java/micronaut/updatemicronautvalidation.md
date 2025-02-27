# Update to Micronaut Validation 4.x

**org.openrewrite.java.micronaut.UpdateMicronautValidation**

_This recipe will add jakarta validation dependency if needed, migrate from javax.validation if needed, and update micronaut validation dependencies._

## Recipe source

[GitHub](https://github.com/openrewrite/rewrite-micronaut/blob/main/src/main/resources/META-INF/rewrite/micronaut3-to-4.yml), [Issue Tracker](https://github.com/openrewrite/rewrite-micronaut/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite.recipe/rewrite-micronaut/2.1.9/jar)

* groupId: org.openrewrite.recipe
* artifactId: rewrite-micronaut
* version: 2.1.9

{% hint style="info" %}
This recipe is composed of more than one recipe. If you want to customize the set of recipes this is composed of, you can find and copy the GitHub source for the recipe from the link above.
{% endhint %}

## Usage

This recipe has no required configuration options. It can be activated by adding a dependency on `org.openrewrite.recipe:rewrite-micronaut:2.1.9` in your build file or by running a shell command (in which case no build changes are needed): 
{% tabs %}
{% tab title="Gradle" %}
1. Add the following to your `build.gradle` file:
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("6.6.2")
}

rewrite {
    activeRecipe("org.openrewrite.java.micronaut.UpdateMicronautValidation")
}

repositories {
    mavenCentral()
}

dependencies {
    rewrite("org.openrewrite.recipe:rewrite-micronaut:2.1.9")
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
        rewrite("org.openrewrite.recipe:rewrite-micronaut:2.1.9")
    }
    rewrite {
        activeRecipe("org.openrewrite.java.micronaut.UpdateMicronautValidation")
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
            <recipe>org.openrewrite.java.micronaut.UpdateMicronautValidation</recipe>
          </activeRecipes>
        </configuration>
        <dependencies>
          <dependency>
            <groupId>org.openrewrite.recipe</groupId>
            <artifactId>rewrite-micronaut</artifactId>
            <version>2.1.9</version>
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
mvn -U org.openrewrite.maven:rewrite-maven-plugin:run -Drewrite.recipeArtifactCoordinates=org.openrewrite.recipe:rewrite-micronaut:RELEASE -Drewrite.activeRecipes=org.openrewrite.java.micronaut.UpdateMicronautValidation
```
{% endcode %}
{% endtab %}
{% tab title="Moderne CLI" %}
You will need to have configured the [Moderne CLI](https://docs.moderne.io/moderne-cli/cli-intro) on your machine before you can run the following command.

{% code title="shell" %}
```shell
mod run . --recipe UpdateMicronautValidation
```
{% endcode %}
{% endtab %}
{% endtabs %}

## Definition

{% tabs %}
{% tab title="Recipe List" %}
* [Rename package name](../../java/changepackage.md)
  * oldPackageName: `javax.validation`
  * newPackageName: `jakarta.validation`
  * recursive: `true`
* [Remove a Gradle or Maven dependency](../../java/dependencies/removedependency.md)
  * groupId: `io.micronaut`
  * artifactId: `micronaut-validation`
* [Remove Maven annotation processor path](../../java/micronaut/removeannotationprocessorpath.md)
  * groupId: `io.micronaut`
  * artifactId: `micronaut-validation`
* [Add Gradle or Maven dependency](../../java/dependencies/adddependency.md)
  * groupId: `io.micronaut.validation`
  * artifactId: `micronaut-validation`
  * onlyIfUsing: `jakarta.validation.constraints.*`
  * configuration: `implementation`
  * scope: `compile`
* [Add Gradle dependency](../../gradle/adddependency.md)
  * groupId: `io.micronaut.validation`
  * artifactId: `micronaut-validation-processor`
  * configuration: `annotationProcessor`
  * onlyIfUsing: `jakarta.validation.constraints.*`
* [Add Maven annotation processor path](../../java/micronaut/addannotationprocessorpath.md)
  * groupId: `io.micronaut.validation`
  * artifactId: `micronaut-validation-processor`
  * version: `${micronaut.validation.version}`
  * onlyIfUsing: `jakarta.validation.constraints.*`
  * exclusions: `[io.micronaut:micronaut-inject]`

{% endtab %}

{% tab title="Yaml Recipe List" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: org.openrewrite.java.micronaut.UpdateMicronautValidation
displayName: Update to Micronaut Validation 4.x
description: This recipe will add jakarta validation dependency if needed, migrate from javax.validation if needed, and update micronaut validation dependencies.
recipeList:
  - org.openrewrite.java.ChangePackage:
      oldPackageName: javax.validation
      newPackageName: jakarta.validation
      recursive: true
  - org.openrewrite.java.dependencies.RemoveDependency:
      groupId: io.micronaut
      artifactId: micronaut-validation
  - org.openrewrite.java.micronaut.RemoveAnnotationProcessorPath:
      groupId: io.micronaut
      artifactId: micronaut-validation
  - org.openrewrite.java.dependencies.AddDependency:
      groupId: io.micronaut.validation
      artifactId: micronaut-validation
      onlyIfUsing: jakarta.validation.constraints.*
      configuration: implementation
      scope: compile
  - org.openrewrite.gradle.AddDependency:
      groupId: io.micronaut.validation
      artifactId: micronaut-validation-processor
      configuration: annotationProcessor
      onlyIfUsing: jakarta.validation.constraints.*
  - org.openrewrite.java.micronaut.AddAnnotationProcessorPath:
      groupId: io.micronaut.validation
      artifactId: micronaut-validation-processor
      version: ${micronaut.validation.version}
      onlyIfUsing: jakarta.validation.constraints.*
      exclusions: [io.micronaut:micronaut-inject]

```
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://app.moderne.io/recipes/org.openrewrite.java.micronaut.UpdateMicronautValidation)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.

## Contributors
[Jeremy Grelle](mailto:grellej@unityfoundation.io)
