# Development Environment Setup

This is a guide on how to set-up your local development environment to contribute to cineast.

---

# Note

**This guide w.r.t. the [`multi-module` branch](https://github.com/vitrivr/cineast/tree/multi-module).**

---

## Prerequisites

It is expected that you have a JDK installed.
We recommend one provided by [Open JDK](https://openjdk.java.net/install/).
Minimal version is JDK for Java SE 8.

Furthermore, you also have to clone the storage layer, [CottontailDB](https://github.com/ppanopticon/cottontaildb).
As of CottontailDB's [current version](https://github.com/ppanopticon/cottontaildb/commit/bc25f6be57b93f0658404025706204ff5f24f830), the steps to prepare your local CottontailDB instance are as follows:

1. Clone [CottontailDB](https://github.com/ppanopticon/cottontaildb.git):

```
git clone --recursive https://github.com/ppanopticon/cottontaildb.git
```

2. Setup and build CottontailDB:

```
$> ./gradlew clean generateProto generateGrammarSource build
```

3. Run CottontailDB

```
$> java -jar build/libs/cottontaildb.jar
```

0. Whenever required, update the submodules:

```
$> git submodule update --init --recursive
```

## Setup

As of now, you have set-up CottontailDB which is running on its default port.
These are your next steps:

1. Clone [Cineast](https://github.com/vitrivr/cineast.git)

```
$> git clone --recursive https://github.com/vitrivr/cineast.git
```

2. Build Cineast

```
$> ./gradlew clean generateProto build
```

By now, you should have all the required dependencies and preparation steps performed.
To actually test / debug cineast now, you would use

`org.vitrivr.cineast.api.Main` as main class.

It has **one mandatory argument**; the config (`cineast.json`).

__More coming soon(tm)__