# `MavenSharedStringUtils` Refaster recipes

**org.openrewrite.java.migrate.maven.shared.MavenSharedStringUtilsRecipes**

_Refaster template recipes for `org.openrewrite.java.migrate.maven.shared.MavenSharedStringUtils`._

## Recipe source

[GitHub](https://github.com/openrewrite/rewrite-migrate-java/blob/main/src/main/java/org/openrewrite/java/migrate/maven/shared/MavenSharedStringUtils.java), [Issue Tracker](https://github.com/openrewrite/rewrite-migrate-java/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite.recipe/rewrite-migrate-java/2.5.0/jar)

* groupId: org.openrewrite.recipe
* artifactId: rewrite-migrate-java
* version: 2.5.0

{% hint style="info" %}
This recipe is composed of more than one recipe. If you want to customize the set of recipes this is composed of, you can find and copy the GitHub source for the recipe from the link above.
{% endhint %}

## Usage

This recipe has no required configuration options. It can be activated by adding a dependency on `org.openrewrite.recipe:rewrite-migrate-java:2.5.0` in your build file or by running a shell command (in which case no build changes are needed): 
{% tabs %}

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
            <recipe>org.openrewrite.java.migrate.maven.shared.MavenSharedStringUtilsRecipes</recipe>
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
mvn -U org.openrewrite.maven:rewrite-maven-plugin:run -Drewrite.recipeArtifactCoordinates=org.openrewrite.recipe:rewrite-migrate-java:RELEASE -Drewrite.activeRecipes=org.openrewrite.java.migrate.maven.shared.MavenSharedStringUtilsRecipes
```
{% endcode %}
{% endtab %}
{% tab title="Moderne CLI" %}
You will need to have configured the [Moderne CLI](https://docs.moderne.io/moderne-cli/cli-intro) on your machine before you can run the following command.

{% code title="shell" %}
```shell
mod run . --recipe MavenSharedStringUtilsRecipes
```
{% endcode %}
{% endtab %}
{% endtabs %}

## Definition

{% tabs %}
{% tab title="Recipe List" %}
* [Replace `StringUtils.abbreviate(String, int)` with JDK internals](../../../../java/migrate/maven/shared/mavensharedstringutilsrecipes$abbreviaterecipe.md)
* [Replace `StringUtils.capitalise(String)` with JDK internals](../../../../java/migrate/maven/shared/mavensharedstringutilsrecipes$capitaliserecipe.md)
* [Replace `StringUtils.defaultString(Object)` with JDK internals](../../../../java/migrate/maven/shared/mavensharedstringutilsrecipes$defaultstringrecipe.md)
* [Replace `StringUtils.defaultString(Object, String)` with JDK internals](../../../../java/migrate/maven/shared/mavensharedstringutilsrecipes$defaultstringfallbackrecipe.md)
* [Replace `StringUtils.deleteWhitespace(String)` with JDK internals](../../../../java/migrate/maven/shared/mavensharedstringutilsrecipes$deletewhitespacerecipe.md)
* [Replace `StringUtils.equalsIgnoreCase(String, String)` with JDK internals](../../../../java/migrate/maven/shared/mavensharedstringutilsrecipes$equalsignorecaserecipe.md)
* [Replace `StringUtils.equals(String, String)` with JDK internals](../../../../java/migrate/maven/shared/mavensharedstringutilsrecipes$equalsrecipe.md)
* [Replace `StringUtils.lowerCase(String)` with JDK internals](../../../../java/migrate/maven/shared/mavensharedstringutilsrecipes$lowercaserecipe.md)
* [Replace `StringUtils.replace(String, String, String)` with JDK internals](../../../../java/migrate/maven/shared/mavensharedstringutilsrecipes$replacerecipe.md)
* [Replace `StringUtils.reverse(String)` with JDK internals](../../../../java/migrate/maven/shared/mavensharedstringutilsrecipes$reverserecipe.md)
* [Replace `StringUtils.split(String)` with JDK internals](../../../../java/migrate/maven/shared/mavensharedstringutilsrecipes$splitrecipe.md)
* [Replace `StringUtils.strip(String)` with JDK internals](../../../../java/migrate/maven/shared/mavensharedstringutilsrecipes$striprecipe.md)
* [Replace `StringUtils.trim(String)` with JDK internals](../../../../java/migrate/maven/shared/mavensharedstringutilsrecipes$trimrecipe.md)
* [Replace `StringUtils.upperCase(String)` with JDK internals](../../../../java/migrate/maven/shared/mavensharedstringutilsrecipes$uppercaserecipe.md)

{% endtab %}

{% tab title="Yaml Recipe List" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: org.openrewrite.java.migrate.maven.shared.MavenSharedStringUtilsRecipes
displayName: `MavenSharedStringUtils` Refaster recipes
description: Refaster template recipes for `org.openrewrite.java.migrate.maven.shared.MavenSharedStringUtils`.
recipeList:
  - org.openrewrite.java.migrate.maven.shared.MavenSharedStringUtilsRecipes$AbbreviateRecipe
  - org.openrewrite.java.migrate.maven.shared.MavenSharedStringUtilsRecipes$CapitaliseRecipe
  - org.openrewrite.java.migrate.maven.shared.MavenSharedStringUtilsRecipes$DefaultStringRecipe
  - org.openrewrite.java.migrate.maven.shared.MavenSharedStringUtilsRecipes$DefaultStringFallbackRecipe
  - org.openrewrite.java.migrate.maven.shared.MavenSharedStringUtilsRecipes$DeleteWhitespaceRecipe
  - org.openrewrite.java.migrate.maven.shared.MavenSharedStringUtilsRecipes$EqualsIgnoreCaseRecipe
  - org.openrewrite.java.migrate.maven.shared.MavenSharedStringUtilsRecipes$EqualsRecipe
  - org.openrewrite.java.migrate.maven.shared.MavenSharedStringUtilsRecipes$LowercaseRecipe
  - org.openrewrite.java.migrate.maven.shared.MavenSharedStringUtilsRecipes$ReplaceRecipe
  - org.openrewrite.java.migrate.maven.shared.MavenSharedStringUtilsRecipes$ReverseRecipe
  - org.openrewrite.java.migrate.maven.shared.MavenSharedStringUtilsRecipes$SplitRecipe
  - org.openrewrite.java.migrate.maven.shared.MavenSharedStringUtilsRecipes$StripRecipe
  - org.openrewrite.java.migrate.maven.shared.MavenSharedStringUtilsRecipes$TrimRecipe
  - org.openrewrite.java.migrate.maven.shared.MavenSharedStringUtilsRecipes$UppercaseRecipe

```
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://app.moderne.io/recipes/org.openrewrite.java.migrate.maven.shared.MavenSharedStringUtilsRecipes)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
