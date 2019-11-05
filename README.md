# Managing Concurrent Requests in C#
Demonstrates how to execute multiple concurrent requests asynchronously while controlling the level of parallelism.

Contributors: [João Reis](https://github.com/joao-r-reis) copied from [here](https://github.com/datastax/csharp-driver/tree/master/examples/ConcurrentExecutions/ExecuteInLoop)

## Objectives

* To demonstrate how to specify manage concurrent asynchronous requests while managing the level of parallelism
  
## Project Layout

* [Program.cs](Program.cs) - The main application file containing the logic for managing the number of simultaneous requests.

## How this Sample Works
A description of how this sample works and how it demonstrates the objectives outlined above

## Setup and Running

### Prerequisites

* .NET Core 2.1
* A DDAC/C*/DSE Cluster running on localhost

If you do not currently have a DDAC/C*/DSE cluster available you can start a DDAC cluster using Docker via the following command:

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

