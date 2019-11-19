# Concurrent Requests in C#
This example shows how execute multiple concurrent requests with Apache Cassandra™ using the [C# DataStax Driver](https://docs.datastax.com/en/developer/csharp-driver/latest).

Contributors: [João Reis](https://github.com/joao-r-reis) - derived from [here](https://github.com/datastax/csharp-driver/tree/master/examples/ConcurrentExecutions/ExecuteInLoop)

## Objectives

* How to execute async concurrent requests while managing parallelism using the C# DataStax Driver
  
## Project Layout

* [Program.cs](Program.cs) - The main application file containing the logic for managing the number of simultaneous requests.

## How this Works
This example creates a single `tbl_sample_kv` table in the `examples` keyspace and writes records to that table asynchronously while capping the max in-flight requests based on the configured concurrency level.

## Setup and Running

### Prerequisites

* .NET Core 2.1
* A Cassandra, DDAC, DSE database running ( docker is a nice option for local install - [see docs](https://docs.datastax.com/en/docker/doc/docker/dockerQuickStart.html) )

If you do not currently have a C*/DDAC/DSE cluster available you can start a DDAC cluster using Docker via the following command:

```docker run -e DS_LICENSE=accept --name ddac -p 127.0.0.1:9042:9042 -d datastax/ddac ```

If you have a DDAC/C*/DSE cluster but it is not located on localhost you need to change the contact point address located on line 33 to point to your cluster IP.

```.AddContactPoint("XX.XX.XX.XX")```


### Running
From the root directory of this project, first run the following command to restore the dependencies:

`dotnet restore`

Once the restore has completed run the following command to build the application:

`dotnet build`

Finally to run the application use the following command:

`dotnet run`

When running you should see output similar to the following:

```MaxConcurrencyLevel=32  TotalLength=10000
Executing 10000 queries with a concurrency level of 32, i.e., 32 tasks. Each task will process up to 313 operations.
Finished executing 10000 queries with a concurrency level of 32.```

