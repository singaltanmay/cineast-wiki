# Development Environment Setup

This is a guide on how to set-up your local development environment to contribute to cineast.

---

# Note

**This guide is w.r.t. the [`dev` branch](https://github.com/vitrivr/cineast/tree/dev).**

---

## Prerequisites

It is expected that you have a JDK installed.
We recommend one provided by [Open JDK](https://openjdk.java.net/install/). Please develop on JDK 11+.

Furthermore, you also have to clone the storage layer, [CottontailDB](https://github.com/ppanopticon/cottontaildb).
Setup cottontail as follows:

1. Clone [CottontailDB](https://github.com/ppanopticon/cottontaildb.git):

```
git clone --recursive https://github.com/ppanopticon/cottontaildb.git
```
(If you've already cloned cottontailDB without the recursive flag, execute ```git submodule update --init --recursive```)

2. Setup and build CottontailDB:

```
$> ./gradlew generateProto run
```

_Windows users beware! Adopt the configuration for windows beforehand by changing the_ `forceUnmapMappedFiles` _property to_ `true`.

## Setup

As of now, you have set-up CottontailDB which is running on its default port.
These are your next steps:

1. Clone [Cineast](https://github.com/vitrivr/cineast.git)

```
$> git clone --recursive https://github.com/vitrivr/cineast.git
```
(If you've already cloned cineast without the recursive flag, execute ```git submodule update --init --recursive```)
4. Open `build.gradle` with your IDE. This requires the IDE supports [Gradle].
5. Generate the protobuf bindings using Gradle:
```
$> ./gradlew clean generateProto
```

You're now ready to develop!