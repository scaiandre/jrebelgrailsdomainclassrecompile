# jrebelgrailsdomainclassrecompile
grails create-app domclasstest
grails create-domain-class Book
grails create-domain-class Author

Add this to build.gradle to make sure gradle and IntelliJ use the same paths for groovy code:
```
idea {
    module {
        inheritOutputDirs = false
        outputDir = compileGroovy.destinationDir
        testOutputDir = compileTestGroovy.destinationDir
    }
}
```