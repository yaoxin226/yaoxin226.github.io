---
---

# Properties and Environment in JVM

## Properties

System properties are set on the java command line using the `-DpropertyNane=value` syntax. They can also be added at runtime using `System.setProperiy(name, value)` or via the various `System.getProperties().load()`

## Environment

Environment variables are set in the OS, eg in linux `export JAVA_HOME=/usr/share/java`. And unlike properties, may not be set at runtime.

## See more

[stack overflow question](http://stackoverflow.com/questions/7054972/java-system-properties-and-environment-variables)
