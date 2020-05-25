---
layout: post
title:  "2020-03-18-gRPc_android.markdown"
date:   2020-03-18 12:11:30 +0800

1. .proto
```

// The greeting service definition.
service Greeter {
  // Sends a greeting
  rpc SayHello (HelloRequest) returns (HelloReply) {}
}

// The request message containing the user's name.
message HelloRequest {
  string name = 1;
}

// The response message containing the greetings
message HelloReply {
  string message = 1;
}

```

2. java
```
ManagedChannel mChannel = ManagedChannelBuilder.forAddress(host, port).usePlaintext(true).build();
AbstractStub stub = RouteGuideGrpc.newBlockingStub(mChannel);

HelloRequest message = HelloRequest.newBuilder().setName(mMessage).build();
HelloReply reply = stub.sayHello(message);
```
3. gradle
```
apply plugin: 'com.google.protobuf'
...
protobuf {
        // Configure the protoc executable
        protoc {
            // Download from repositories
            artifact = 'com.google.protobuf:protoc:3.0.0' // 这里可以手工指定 path = '/usr/local/bin/protoc'
        }
        plugins {
            // Optional: an artifact spec for a protoc plugin, with "grpc" as
            // the identifier, which can be referred to in the "plugins"
            // container of the "generateProtoTasks" closure.
            javalite {
                artifact = "com.google.protobuf:protoc-gen-javalite:3.0.0"
            }
            grpc {
                artifact = 'io.grpc:protoc-gen-grpc-java:1.0.0' //grpc-java版本
            }
        }
        generateProtoTasks {
            all().each { task ->
                task.plugins {
                    javalite {}
                    grpc {
                        // Options added to --grpc_out
                        option 'lite' //生成类型
                    }
                }
            }
        }
    }
```
4. 可以使用okhttp进行加密验证
```
managedChannel = OkHttpChannelBuilder.forAddress(host, port)
                    .hostnameVerifier(new SSLHostnameVerifier())
                    .sslSocketFactory(SSLSocketLoader.createSSLSocketFactory())
                    .build();
```

参考文件

 https://grpc.io/docs/quickstart/java/
 






