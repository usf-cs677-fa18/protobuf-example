# Protocol Buffers Example

This extends the Project 1 template code with a simple server and client that send messages via Protocol Buffers.

To work with Protocol Buffers on your own machine, you'll need to install the ```protoc``` compiler. Install via your package manager:

* **protobuf** on homebrew 
* **protobuf-compiler** on RedHat-based distributions

...or download via the [Protocol Buffers Homepage](https://developers.google.com/protocol-buffers/)

## Running the Example

```
# Compile and package:
$ mvn clean package

# Run a test 'server':
$ java -cp target/dfs-1.0.jar edu.usfca.cs.dfs.StorageNode
Starting storage node on silicon...
Listening...

# Then, in another terminal, start a 'client':
$ java -cp target/dfs-1.0.jar edu.usfca.cs.dfs.Client
```

The client will return after sending a single message to the server (assuming both client and server are on the same machine!). The server should print "Storing file name: my_file.txt" if the message was sent successfully.

## Workflow

* Add the library jar to your project
* Create .proto files that define your communications
* Compile them with protoc to Java classes
  * This is where you could also generate Python, Scala, C#, etc.
* Use the classes to encapsulate your communications

## Hints / Best Practices

* You may want to put all your message types in one (or two) .proto files
* An outer class is generated for each file, with each message you define represented by inner classes
  * my_proto.proto -> MyProto.java
* Since your components will send/receive multiple message types, you also need a message Wrapper
  * This gives each message a unique ID
