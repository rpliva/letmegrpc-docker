# Letmegrpc - docker

**letmgrpc-docker** sets up a container running [letmegrpc](https://github.com/gogo/letmegrpc).

## What is letmegrpc

**Letmegrpc** is project which generates a web form GUI from a [grpc](http://www.grpc.io/) definition.

## How to use this image

**letmegrpc** server runs in default container port 8080. 

### Default static configuration

`docker run -it --rm -p 8080:8080 rudiscz/letmegrpc`

If you run image without any configuration (except exposing the port) you can hit http://localhost:8080/TestService/Foo in your browser and a demo page will be displayed.

### Load service proto defition via shared folder

`docker run -it --rm -p 8080:8080 -v /docker/host/dir:/var/letmegrpc/protos -e PROTO_FILE file.proto -e SERVICE_ADDRESS localhost:8888 rudiscz/letmegrpc`

This image has specified mounting point `/var/letmegrpc/protos` where the server expects proto files. The mounting point is map to the local folder `/docker/host/dir`. 

To specified which proto file should be used the image reads environment variable `PROTO_FILE`. A server url which hosts gRPC API service is defined in environment variable `SERVICE_ADDRESS`.

### Create own image based this one

TBD

## Limitations

- it will only work for single file proto specs
- RPC methods must to start with capital case letter
