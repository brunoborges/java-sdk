## Dapr SDK for Java

This is the Dapr SDK for Java, based on the auto-generated proto client.<br>

For more info on Dapr and gRPC, visit [this link](https://github.com/dapr/docs/tree/master/howto/create-grpc-app).

### Installing

The client will generate gRPC Client and Protobuf classes during build. 

Make sure to clone this repository including the submodules:

```sh
git clone --recurse-submodules https://github.com/dapr/java-sdk.git
```

Then head over to build the Maven project:

```sh
# make sure you are in the `java-sdk` directory.
mvn install
```

### Running an example
```sh
cd examples/
dapr run --protocol grpc --grpc-port 50001 -- mvn exec:java -Dexec.mainClass=io.dapr.examples.Example
```

### Creating and publishing the artifacts to Nexus Repository
From the root directory:

```sh
mvn package
mvn deploy:deploy-file -DgeneratePom=false -DrepositoryId=nexus -Durl=http://localhost:8081/repository/maven-releases -DpomFile=pom.xml -Dfile=target/client-0.1.0-preview.jar
```
For more documentation reference :

https://maven.apache.org/plugins/maven-deploy-plugin

https://help.sonatype.com/repomanager3/user-interface/uploading-components

### Maven Module version management
To increase the version of all modules and pom files, run the following commands:

```sh
mvn versions:set -DnewVersion="0.1.0-preview02"
mvn versions:commit
```
