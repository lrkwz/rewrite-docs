# Find and replace

**org.openrewrite.text.FindAndReplace**

_Simple text find and replace. When the original source file is a language-specific Lossless Semantic Tree, this operation irreversibly converts the source file to a plain text file. Subsequent recipes will not be able to operate on language-specific type._

## Recipe source

[GitHub](https://github.com/openrewrite/rewrite/blob/main/rewrite-core/src/main/java/org/openrewrite/text/FindAndReplace.java), [Issue Tracker](https://github.com/openrewrite/rewrite/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite/rewrite-core/8.11.5/jar)

* groupId: org.openrewrite
* artifactId: rewrite-core
* version: 8.11.5

## Options

| Type | Name | Description | Example |
| -- | -- | -- | -- |
| `String` | find | The text to find (and replace). | `blacklist` |
| `String` | replace | *Optional*. The replacement text for `find`. This supports multiline strings. | `denylist` |
| `Boolean` | regex | *Optional*. Default false. If true, `find` will be interpreted as a Regular Expression, and capture group contents will be available in `replace`. |  |
| `Boolean` | caseSensitive | *Optional*. If `true` the search will be sensitive to case. Default `false`. |  |
| `Boolean` | multiline | *Optional*. When performing a regex search setting this to `true` allows "^" and "$" to match the beginning and end of lines, respectively. When performing a regex search when this is `false` "^" and "$" will match only the beginning and ending of the entire source file, respectively.Has no effect when not performing a regex search. Default `false`. |  |
| `Boolean` | dotAll | *Optional*. When performing a regex search setting this to `true` allows "." to match line terminators.Has no effect when not performing a regex search. Default `false`. |  |
| `String` | filePattern | *Optional*. A glob expression that can be used to constrain which directories or source files should be searched. Multiple patterns may be specified, separated by a semicolon `;`. If multiple patterns are supplied any of the patterns matching will be interpreted as a match. When not set, all source files are searched.  | `**/*.java` |


## Usage

This recipe has required configuration parameters. Recipes with required configuration parameters cannot be activated directly. To activate this recipe you must create a new recipe which fills in the required parameters. In your `rewrite.yml` create a new recipe with a unique name. For example: `com.yourorg.FindAndReplaceExample`.
Here's how you can define and customize such a recipe within your rewrite.yml:

{% code title="rewrite.yml" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: com.yourorg.FindAndReplaceExample
displayName: Find and replace example
recipeList:
  - org.openrewrite.text.FindAndReplace:
      find: blacklist
      replace: denylist
      filePattern: '**/*.java'
```
{% endcode %}

Now that `com.yourorg.FindAndReplaceExample` has been defined activate it in your build file:
{% tabs %}
{% tab title="Gradle" %}
1. Add the following to your `build.gradle` file:
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("6.6.2")
}

rewrite {
    activeRecipe("com.yourorg.FindAndReplaceExample")
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
            <recipe>com.yourorg.FindAndReplaceExample</recipe>
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
mod run . --recipe FindAndReplace
```
{% endcode %}
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://app.moderne.io/recipes/org.openrewrite.text.FindAndReplace)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.

## Contributors
[Sam Snyder](mailto:sam@moderne.io), [Nick McKinney](mailto:mckinneynicholas@gmail.com), [Tim te Beek](mailto:tim@moderne.io), [Jonathan Schneider](mailto:jkschneider@gmail.com), [Scott Jungling](mailto:scott@moderne.io)
