# Java LSIF indexer

Visit https://lsif.dev/ to learn about LSIF.

## Installation

- Java 1.8 or higher installed on your machine (macOS: `brew cask install java`)
- [Maven](https://maven.apache.org/install.html) (macOS: `brew install maven`)

```
git clone https://github.com/sourcegraph/lsif-java
cd lsif-java
./gradlew installDist
```

## Generating an LSIF dump

**Step 1** Ensure you have a `pom.xml` (Maven projects already have one):

For Gradle projects:

- Add a [`createPom`](https://docs.gradle.org/current/userguide/maven_plugin.html#sec:maven_convention_methods) task

```groovy
task createPom  {
    pom { }.writeTo("pom.xml")
}
```

  - Run `gradle createPom`
  - You should now see `pom.xml` at the top of your project directory

**Step 2** Generate an LSIF dump:

```
<absolute path to lsif-java>/build/install/lsifjava/bin/lsifjava \
  -projectRoot <project directory> \
  -out dump.lsif
```

## Comparison to [Microsoft/lsif-java](https://github.com/Microsoft/lsif-java)

- sourcegraph/lsif-java is ~10x faster
- sourcegraph/lsif-java supports cross-file hovers/definitions/references (Microsoft/lsif-java does not)
- sourcegraph/lsif-java uses [Spoon](https://github.com/INRIA/spoon), which is built on [eclipse.jdt.core](https://github.com/eclipse/eclipse.jdt.core)
- Microsoft/lsif-java uses [eclipse.jdt.ls](https://github.com/eclipse/eclipse.jdt.ls), which is also built on [eclipse.jdt.core](https://github.com/eclipse/eclipse.jdt.core)

See https://github.com/microsoft/lsif-java/issues/61 for the status of collaboration efforts.

## Development

```
./dev
```
