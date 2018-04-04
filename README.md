# bleach ![icon](/src/main/resources/icons/icon_32.png)

Exterminate bugs from your code!

Actually, no, these are just my personal uniform static analysis rules for my projects.

## Motivation

* I keep reusing the same set of rules across my projects so I need them defined in one place.
* The rules themselves are starting to become a separate concern on their own: they are starting to evolve at a different pace from the projects where they're being used.
* My rules are my own! They reflect my personal preferences.

## Strictness

My style guide for test code is a bit less strict than that for production code.

Use the `extra-bleach` profile for the `${project.build.sourceDirectory}` directory. This profile applies the full set of rules (most strict).

Use the `bleach` profile for the `${project.build.testSourceDirectory}` directory. This profile excludes the following rules (less strict):

* **[AvoidStaticImport](http://checkstyle.sourceforge.net/config_imports.html#AvoidStaticImport)**: My test framework of choice, [JUnit](https://junit.org), heavily relies on static methods. A declarative, OO approached would have been ideal but that's what we've got. Avoiding the use of static imports of these junit methods hurts readability of the tests.

* **[MethodName](http://checkstyle.sourceforge.net/config_naming.html#MethodName)**: Test method names should express the test's intent. Although I still enforce javadocs on `@Test` methods, it's still better to have full sentences in these method names so that a) CRs are a bit easier, and b) reading the stack trace when a test fails is also easier.

* **[MultipleStringLiterals](http://checkstyle.sourceforge.net/config_coding.html#MultipleStringLiterals)**: Tests should ideally share no dependencies. Also, having those string attributes declared at the top of the test class just serve as a distraction from what you *really* want to look at: the tests themselves.

* **[AbbreviationAsWordInName](http://checkstyle.sourceforge.net/config_naming.html#AbbreviationAsWordInName)**: Applies mainly to integration tests where the test class' name ends in "IT".

<br/>

<div>Icons made by <a href="http://www.freepik.com" title="Freepik">Freepik</a> from <a href="https://www.flaticon.com/" title="Flaticon">www.flaticon.com</a> is licensed by <a href="http://creativecommons.org/licenses/by/3.0/" title="Creative Commons BY 3.0" target="_blank">CC 3.0 BY</a></div>