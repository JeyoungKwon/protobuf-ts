@protobuf-ts/grpc-transport
===========================

[gRPC](https://grpc.io/) transport for clients generated by [protobuf-ts](https://github.com/timostamm/protobuf-ts/).

Installation:

```shell script
# with npm:
npm install @protobuf-ts/grpc-transport

# with yarn:
yarn add @protobuf-ts/grpc-transport
```


You probably want the protoc plugin as well: 
          
```shell script
# with npm:
npm install -D @protobuf-ts/plugin

# with yarn:
yarn add --dev @protobuf-ts/plugin
```
                       

Usage:
```typescript
const transport = new GrpcTransport({
    host: "localhost:5000",
    channelCredentials: ChannelCredentials.createInsecure(),
});

let client = new HaberdasheryClient(transport);

let {response} = await client.makeHat({ inches: 11 });
console.log("got a small hat! " + response)

let streamingCall = client.makeRowOfHats({ inches: 23 });
for await (let hat of streamingCall.response) {
    console.log("got another hat! " + hat)
}
```


To learn more, please read the [MANUAL](https://github.com/timostamm/protobuf-ts/blob/master/MANUAL.md#grpc-transport).   


