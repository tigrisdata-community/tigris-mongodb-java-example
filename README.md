# Tigris MongoDB compatibility and Java example

## Introduction

Welcome to this [Tigris MongoDB compatibility](https://www.tigrisdata.com/docs/concepts/mongodb-compatibility/) and Java examples repo. This repo aims to show a basic examples of how you can use the power of Tigris MongoDB compatibility with Java.

This project uses [MongoDB Java driver](https://www.mongodb.com/docs/drivers/java/sync/current/).

Tigris MongoDB compatibility supports the MongoDB 6.0+ wire protocol, so any drivers or other components must support this version.

## Prerequisites

- Java JDK 8 to 15.
- Maven 3.6.3.
- A [Tigris Cloud account](https://console.preview.tigrisdata.cloud/signup) or you can [self-host Tigris](https://www.tigrisdata.com/docs/concepts/platform/self-host/)

## Preparing Tigris

1. Create a project in Tigris.
1. Create an application key, and copy the Project Name, Client ID, and Client Secret values.

## Run the examples

Before running the examples, `export` the Tigris connection string and a database name:

```sh
export TIGRIS_CONNECTION_STRING="mongodb://{TIGRIS_CLIENT_ID}:{TIGRIS_CLIENT_SECRET}@m1k.preview.tigrisdata.cloud:27018/?authMechanism=PLAIN&tls=true"
export TIGRIS_PROJECT_NAME="{TIGRIS_PROJECT_NAME}"
```

Replacing `{TIGRIS_CLIENT_ID}` with your Tigris Client ID, `{TIGRIS_CLIENT_SECRET}` with your Tigris Client Secret,
and `{TIGRIS_PROJECT_NAME}` with the name of your Tigris Project. Remember to quote the values.

Next, compile:

```sh
mvn clean compile
```

Test the `HelloMongoDB` hello world example:

```sh
mvn compile exec:java -Dexec.mainClass="com.mongodb.quickstart.HelloMongoDB" -Dexec.cleanupDaemonThreads=false
```

Now you're ready to run the examples:

### Connection

Run the `Connection` class:

```sh
mvn compile exec:java -Dexec.mainClass="com.mongodb.quickstart.Connection" -Dmongodb.uri="$TIGRIS_CONNECTION_STRING" -Dexec.cleanupDaemonThreads=false
```

### CRUD using POJOs

The `MappingPOJO` class show full CRUD functionality using a schema defined via a Java class:

```sh
mvn compile exec:java -Dexec.mainClass="com.mongodb.quickstart.MappingPOJO" -Dmongodb.uri="$TIGRIS_CONNECTION_STRING" -Ddb.name="$TIGRIS_PROJECT_NAME" -Dexec.cleanupDaemonThreads=false
```

## Other examples

Other examples using a dynamic schema can be found below:

Please note: You may need to delete the `grades` collection from the Tigris web console before running the follow examples.

### Create

Run the `Create` class:

```sh
mvn compile exec:java -Dexec.mainClass="com.mongodb.quickstart.Create" -Dmongodb.uri="$TIGRIS_CONNECTION_STRING" -Ddb.name="$TIGRIS_PROJECT_NAME" -Dexec.cleanupDaemonThreads=false
```

### Read

- Run the `Read` class:

```sh
mvn compile exec:java -Dexec.mainClass="com.mongodb.quickstart.Read" -Dmongodb.uri="$TIGRIS_CONNECTION_STRING" -Ddb.name="$TIGRIS_PROJECT_NAME" -Dexec.cleanupDaemonThreads=false
```

### Update

Run the `Update` class:

```sh
mvn compile exec:java -Dexec.mainClass="com.mongodb.quickstart.Update" -Dmongodb.uri="$TIGRIS_CONNECTION_STRING" -Ddb.name="$TIGRIS_PROJECT_NAME" -Dexec.cleanupDaemonThreads=false
```

### Delete

Run the `Delete` class:

```sh
mvn compile exec:java -Dexec.mainClass="com.mongodb.quickstart.Delete" -Dmongodb.uri="$TIGRIS_CONNECTION_STRING" -Ddb.name="$TIGRIS_PROJECT_NAME" -Dexec.cleanupDaemonThreads=false
```

### Aggregation (limited support)

Tigris presently has limited support for Aggregation.

⚠️ The following example does not presently work.

Run the `AggregationFramework` class:

```sh
mvn compile exec:java -Dexec.mainClass="com.mongodb.quickstart.AggregationFramework" -Dmongodb.uri="$TIGRIS_CONNECTION_STRING" -Ddb.name="$TIGRIS_PROJECT_NAME" -Dexec.cleanupDaemonThreads=false
```

### Change streams (⚠️ Not supported)

- Run the `ChangeStreams` class:

```sh
mvn compile exec:java -Dexec.mainClass="com.mongodb.quickstart.ChangeStreams" -Dmongodb.uri="$TIGRIS_CONNECTION_STRING" -Ddb.name="$TIGRIS_PROJECT_NAME" -Dexec.cleanupDaemonThreads=false
```

### Client Side Field Level Encryption (⚠️ Not supported)

Run the `ClientSideFieldLevelEncryption` class:

```sh
mvn compile exec:java -Dexec.mainClass="com.mongodb.quickstart.csfle.ClientSideFieldLevelEncryption" -Dmongodb.uri="$TIGRIS_CONNECTION_STRING" -Ddb.name="$TIGRIS_PROJECT_NAME" -Dexec.cleanupDaemonThreads=false
```

## Where next?

- Find out more about [Tigris MongoDB compatibility](https://www.tigrisdata.com/docs/concepts/mongodb-compatibility/)
- Join the [Tigris Discord](https://www.tigrisdata.com/discord/)

Additional MongoDB resources:

- [MongoDB & Java - CRUD Operations Tutorial](https://developer.mongodb.com/quickstart/java-setup-crud-operations)
- [Java - Mapping POJOs](https://developer.mongodb.com/quickstart/java-mapping-pojos)
- [Java - Aggregation Pipeline](https://developer.mongodb.com/quickstart/java-aggregation-pipeline)
- [Java - Change Streams](https://developer.mongodb.com/quickstart/java-change-streams)
- [Java - Client Side Field Level Encryption](https://developer.mongodb.com/quickstart/java-client-side-field-level-encryption/)

# Credits

The original repository author: Maxime Beugnet <maxime@mongodb.com>
