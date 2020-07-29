# Environment Setup

This is a guide on how to set-up your local environment to contribute to and use cineast.
## Prerequisites

It is expected that you have a JDK installed.
We recommend one provided by [Open JDK](https://openjdk.java.net/install/). Please develop on JDK 11+.

Furthermore, you also have to setup the storage layer, [CottontailDB](https://github.com/vitrivr/cottontaildb). Consult its documentation for setup and installation.

## Setup

You should now have a running instance of CottontailDB. To install cineast, proceed:

1. Clone [Cineast](https://github.com/vitrivr/cineast.git)

```
$> git clone --recursive https://github.com/vitrivr/cineast.git
```
(If you've already cloned cineast without the recursive flag, execute ```git submodule update --init --recursive```)

4. Open Cineast with your IDE supporting Gradle (we recommend IntelliJ)

5. Generate the protobuf bindings using Gradle:
```
$> ./gradlew clean generateProto
```

2. Download external files, such as codebooks by executing
```
$> gradlew getExternalFiles
````
You're now ready! Proceed with the [Getting Started](https://github.com/vitrivr/cineast/wiki/Getting-Started) page