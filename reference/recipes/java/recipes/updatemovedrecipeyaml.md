# Update moved package recipe in yaml file

**org.openrewrite.java.recipes.UpdateMovedRecipeYaml**

_Update moved package recipe in yaml file._

## Recipe source

[GitHub](https://github.com/openrewrite/rewrite/blob/main/rewrite-java/src/main/java/org/openrewrite/java/recipes/UpdateMoved.java), [Issue Tracker](https://github.com/openrewrite/rewrite/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite/rewrite-java/8.11.5/jar)

* groupId: org.openrewrite
* artifactId: rewrite-java
* version: 8.11.5

## Options

| Type | Name | Description | Example |
| -- | -- | -- | -- |
| `String` | oldRecipeFullyQualifiedClassName | The fully qualified className of recipe moved from a old package. | `org.openrewrite.java.cleanup.UnnecessaryCatch` |
| `String` | newRecipeFullyQualifiedClassName | The fully qualified className of recipe moved to a new package. | `org.openrewrite.staticanalysis.UnnecessaryCatch` |


## Usage

This recipe has required configuration parameters. Recipes with required configuration parameters cannot be activated directly. To activate this recipe you must create a new recipe which fills in the required parameters. In your `rewrite.yml` create a new recipe with a unique name. For example: `com.yourorg.UpdateMovedRecipeYamlExample`.
Here's how you can define and customize such a recipe within your rewrite.yml:

{% code title="rewrite.yml" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: com.yourorg.UpdateMovedRecipeYamlExample
displayName: Update moved package recipe in yaml file example
recipeList:
  - org.openrewrite.java.recipes.UpdateMovedRecipeYaml:
      oldRecipeFullyQualifiedClassName: org.openrewrite.java.cleanup.UnnecessaryCatch
      newRecipeFullyQualifiedClassName: org.openrewrite.staticanalysis.UnnecessaryCatch
```
{% endcode %}

Now that `com.yourorg.UpdateMovedRecipeYamlExample` has been defined activate it in your build file:
{% tabs %}
{% tab title="Gradle" %}
1. Add the following to your `build.gradle` file:
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("6.6.2")
}

rewrite {
    activeRecipe("com.yourorg.UpdateMovedRecipeYamlExample")
}

repositories {
    mavenCentral()
}
```
{% endcode %}
2. Run `gradle rewriteRun` to run the recipe.
{% endtab %}
{% tab title="Maven" %}
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
            <recipe>com.yourorg.UpdateMovedRecipeYamlExample</recipe>
          </activeRecipes>
        </configuration>
      </plugin>
    </plugins>
  </build>
</project>
```
{% endcode %}
2. Run `mvn rewrite:run` to run the recipe.
{% endtab %}
{% tab title="Moderne CLI" %}
You will need to have configured the [Moderne CLI](https://docs.moderne.io/moderne-cli/cli-intro) on your machine before you can run the following command.

{% code title="shell" %}
```shell
mod run . --recipe UpdateMovedRecipeYaml
```
{% endcode %}
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://app.moderne.io/recipes/org.openrewrite.java.recipes.UpdateMovedRecipeYaml)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.

## Contributors
[Kun Li](mailto:kun@moderne.io), [Tim te Beek](mailto:tim@moderne.io)
