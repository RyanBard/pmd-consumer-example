# PMD Consumer Example

This is an example project that is using the [maven-pmd-plugin](https://maven.apache.org/plugins/maven-pmd-plugin/).  The purpose of this project is to help test usage of the pmd plugin.

## Prereqs for Mac

I did my testing in OS X.  You can do the testing in the following sections in any OS as long as you have multiple versions of java and manually set your JAVA_HOME before running maven.  I'm using [jenv](http://www.jenv.be/) to manage my java & JAVA_HOME in these examples.

Enable jenv to work with mvnw if you haven't before:
(otherwise, mvnw doesn't respect the version of java jenv is specifying)
https://github.com/gcuisinier/jenv/issues/78

```shell
jenv enable-plugin export
```

## Testing the pmd plugin 

### Java 7

Set jdk1.7:

```shell
jenv local 1.7
```

Confirm the java version maven will use is 1.7:

```shell
./mvnw -version
```

```
Maven home: /Users/ryan/.m2/wrapper/dists/apache-maven-3.5.2-bin/28qa8v9e2mq69covern8vmdkj0/apache-maven-3.5.2
Java version: 1.7.0_51, vendor: Oracle Corporation
Java home: /Library/Java/JavaVirtualMachines/jdk1.7.0_51.jdk/Contents/Home/jre
Default locale: en_US, platform encoding: UTF-8
OS name: "mac os x", version: "10.13.1", arch: "x86_64", family: "mac"
```


Now build with java 7 (the maven profile to target 1.7 will kick in):

```shell
./mvnw clean verify
```

```
[INFO] 
[INFO] <<< maven-pmd-plugin:3.8:check (default) < :pmd @ pmd-consumer-example <<<
[INFO] 
[INFO] 
[INFO] --- maven-pmd-plugin:3.8:check (default) @ pmd-consumer-example ---
[INFO] 
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 2.319 s
[INFO] Finished at: 2017-11-18T16:29:27-05:00
[INFO] Final Memory: 24M/310M
[INFO] ------------------------------------------------------------------------
```

### Java 8

Set jdk1.8:

```shell
jenv local 1.8
```

Confirm the java version maven will use is 1.8:

```shell
./mvnw -version
```

```
Apache Maven 3.5.2 (138edd61fd100ec658bfa2d307c43b76940a5d7d; 2017-10-18T03:58:13-04:00)
Maven home: /Users/ryan/.m2/wrapper/dists/apache-maven-3.5.2-bin/28qa8v9e2mq69covern8vmdkj0/apache-maven-3.5.2
Java version: 1.8.0_40, vendor: Oracle Corporation
Java home: /Library/Java/JavaVirtualMachines/jdk1.8.0_40.jdk/Contents/Home/jre
Default locale: en_US, platform encoding: UTF-8
OS name: "mac os x", version: "10.13.1", arch: "x86_64", family: "mac"
```


Now build with java 8 (the maven profile to target 1.8 will kick in):

```shell
./mvnw clean verify
```

```
[INFO] 
[INFO] <<< maven-pmd-plugin:3.8:check (default) < :pmd @ pmd-consumer-example <<<
[INFO] 
[INFO] 
[INFO] --- maven-pmd-plugin:3.8:check (default) @ pmd-consumer-example ---
[INFO] 
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 2.610 s
[INFO] Finished at: 2017-11-18T16:29:56-05:00
[INFO] Final Memory: 27M/306M
[INFO] ------------------------------------------------------------------------
```


### Java 9

Set jdk1.9:

```shell
jenv local 9.0
```

Confirm the java version maven will use is 1.9:

```shell
./mvnw -version
```

```
Apache Maven 3.5.2 (138edd61fd100ec658bfa2d307c43b76940a5d7d; 2017-10-18T03:58:13-04:00)
Maven home: /Users/ryan/.m2/wrapper/dists/apache-maven-3.5.2-bin/28qa8v9e2mq69covern8vmdkj0/apache-maven-3.5.2
Java version: 9.0.1, vendor: Oracle Corporation
Java home: /Library/Java/JavaVirtualMachines/jdk-9.0.1.jdk/Contents/Home
Default locale: en_US, platform encoding: UTF-8
OS name: "mac os x", version: "10.13.1", arch: "x86_64", family: "mac"
```


Now build with java 9 (the maven profile to target 1.9 will kick in):

```shell
./mvnw clean verify
```

```
[INFO] >>> maven-pmd-plugin:3.8:check (default) > :pmd @ pmd-consumer-example >>>
[INFO] 
[INFO] --- maven-pmd-plugin:3.8:pmd (pmd) @ pmd-consumer-example ---
[WARNING] The POM for commons-logging:commons-logging:jar:1.1.3 is invalid, transitive dependencies (if any) will not be available, enable debug logging for more details
[INFO] ------------------------------------------------------------------------
[INFO] BUILD FAILURE
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 2.473 s
[INFO] Finished at: 2017-11-18T16:31:22-05:00
[INFO] Final Memory: 21M/71M
[INFO] ------------------------------------------------------------------------
[ERROR] Failed to execute goal org.apache.maven.plugins:maven-pmd-plugin:3.8:pmd (pmd) on project pmd-consumer-example: Execution pmd of goal org.apache.maven.plugins:maven-pmd-plugin:3.8:pmd failed: org.apache.maven.reporting.MavenReportException: Unsupported targetJdk value '1.9'. -> [Help 1]
[ERROR] 
[ERROR] To see the full stack trace of the errors, re-run Maven with the -e switch.
[ERROR] Re-run Maven using the -X switch to enable full debug logging.
[ERROR] 
[ERROR] For more information about the errors and possible solutions, please read the following articles:
[ERROR] [Help 1] http://cwiki.apache.org/confluence/display/MAVEN/PluginExecutionException
```
