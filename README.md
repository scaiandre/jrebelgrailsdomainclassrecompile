# jrebelgrailsdomainclassrecompile
https://github.com/scaiandre/jrebelgrailsdomainclassrecompile

* grails create-app domclasstest
* grails create-domain-class Book
* grails create-domain-class Author

* Add this to build.gradle to make sure gradle and IntelliJ use the same paths for groovy code:
```
idea {
    module {
        inheritOutputDirs = false
        outputDir = compileGroovy.destinationDir
        testOutputDir = compileTestGroovy.destinationDir
    }
}
```

* Add this to Author.groovy
```
    public static final int testy = 1

```

* Start JRebel Debug in IntelliJ of gradle task "bootRun"
* Change testy constant in Author.groovy to this 
```
    public static final int testy = 2

```
* PROBLEM => Instead of just recompiling Author.groovy, also Book.groovy gets recompiled and reloaded by JRebel. We have a project with >220 domain classes. This takes longer than just restarting the application. I also noticed in that big project the whole build/classes tree gets rebuilt sometimes. 
* Is this an IntelliJ issue or a JRebel issue? Using IntelliJ 2020.3 and this Jrebel nightly ~/.jrebel/nightly_cache/202011301400/jrebel/jrebel.jar
