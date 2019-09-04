# Grab

## Task in progress: Integrate rest apis using emicklei/go-restful

Grab: Online store based on Go microservices, GRPC, protobuf, postgresql, elastic search and GraphQL.

The underlying source code for the article [Using GraphQL API Gateway for Microservices in Go](https://outcrawl.com/go-graphql-gateway-microservices).

## create pb files
```
$ go generate catalog/server.go
$ go generate account/server.go
$ go generate order/server.go
```

## create gqlgen generated file [DO NOT DO THIS]
Note: (first make backup of graph folder before doing so or please do not re-generate this again as this will remove all the modifications made to the resolvers inside this folder, you will be bombartded with errors)
```
$ sudo go generate graphql/graph/graph.go
```

## update go.mod and go.sum files
```
$ go mod tidy
```

## Build
install all the dependencies from go.mod into vendor folder
```
$ go mod vendor
$ docker-compose up -d --build
```

Open <http://localhost:8000/playground> in your browser.
                            or
Try sending Post request for query and mutation to <http://localhost:8000/graphql> in postman.

## Issue with accesing URL?
Try changing graphql ports in docker-compose from "8000:8080" to "8000"

## Accesing postgres from docker container

```
$ docker ps (copy container id where postgres is running)
$ docker exec -it <postgres-container-id-05b3a3471f6f> bash
$root@05b3a3471f6f:/# psql -U <databasename-grab>
$ \dt (look for schema name and table name)
$ SELECT * FROM <schema-name>.<table-name>; (Example: SELECT * FROM public.orders;)
$ \q
$ exit
```
