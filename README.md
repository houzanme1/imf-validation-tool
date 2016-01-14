Interoperable Master Format (IMF) Validation Tool

-------------------------------------------------------------------------------
INTRODUCTION
-------------------------------------------------------------------------------

The IMF Validation Tool is used to verify the contents of a IMF package.

Verification is performed in four phases in the following order:
* Verify AssetMap.xml file
* Verify PackingList file
* Verify CPL files
* Verify essence files

If errors occur in some phase, then the following phases are skipped.

-------------------------------------------------------------------------------
DEPENDENCIES
-------------------------------------------------------------------------------

The IMF Validation has dependencies on following libraries:
* log4j
* slf4j-api
* slf4j-log4j12
* MXFLibrary
* junit

-------------------------------------------------------------------------------
PACKAGE STRUCTURE
-------------------------------------------------------------------------------

The IMF Validation containts packages in following structure:
```
src/test (test folder)
        com.sferalabs.imf.test
src/app (IMF application folder)
        com.sferalabs.imf.exception
src/imf (IMF library folder)
        com.sferalabs.imf.exception
        com.sferalabs.imf.model.assetmap
        com.sferalabs.imf.model.compositionplaylist
        com.sferalabs.imf.model.imfpackage
        com.sferalabs.imf.model.packinglist
        com.sferalabs.imf.saxhandler
        com.sferalabs.imf.util
        com.sferalabs.imf.validation
        com.sferalabs.imf.xsd
        com.sferalabs.imf.xsd.schema
```

-------------------------------------------------------------------------------
IMF LIBRARY CLASS STRUCTURE
-------------------------------------------------------------------------------

Please refer to **javadoc** for more details on class usage.


-------------------------------------------------------------------------------
BUILD
-------------------------------------------------------------------------------

Download gradle 2.3 and up should work.

The code base is IDE neutral. IDE specific files can be generated with gradle from build.gradle.
* `gradle eclipse` (generate eclipse project files)
* `gradle idea` (intellij)

Please don't check in IDE specific files.

Always add dependencies to `build.gradle`. `libs/` should only be used for dependencies that are not available from Maven repos.

Building imf binary
```
gradle clean build
```

Get the jar from the build directory. It will typically be here:
```
build/libs/imf-validation-library-<VERSION>.jar: library jar file
build/libs/imf-validation-tool-<VERSION>.jar: executable imf validation tool jar file
```

-------------------------------------------------------------------------------
RUNNING
-------------------------------------------------------------------------------
In order to run the IMF verifier, use the following (or an equivalent):

```
java -jar imf-validation-tool.jar <OPTIONS>
```

Usage information can be obtained by using:

```
java -jar imf-validation-tool.jar -h
```

At present, this will output the following:

```
Usage:
-p,--package    <folder>    package to verify (should be used only one time)
-d,--depend     <folder>    dependent package (can be used multiple times to specify multiple dependent packages)
--hash-check                perform files hash validation (disabled by default)
--assetmap-xsd              specify asset map xsd
--packinglist-xsd           specify packinglist xsd
--coreconstraints-xsd       specify core constraints xsd
-v,--verbose                print debug information during validation
-h,--help                   show usage information
```

-------------------------------------------------------------------------------
NOTES
-------------------------------------------------------------------------------
At present, imf-validation-tool is being developed using the following versions of tools:
```
    $ java -version
    java version "1.8.0_31"
    Java(TM) SE Runtime Environment (build 1.8.0_31-b13)
    Java HotSpot(TM) 64-Bit Server VM (build 25.31-b07, mixed mode)
```
