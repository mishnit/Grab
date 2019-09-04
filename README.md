# Grab

## Task in progress: Integrate rest apis using emicklei/go-restful

Grab: Online store based on Go microservices, GRPC, protobuf, postgresql, elastic search and GraphQL.

The underlying source code for the article [Using GraphQL API Gateway for Microservices in Go](https://outcrawl.com/go-graphql-gateway-microservices).

## create pb files
```
go generate catalog/server.go
go generate account/server.go
go generate order/server.go
```

## create gqlgen generated file [DO NOT DO THIS]
Note: (first make backup of graph folder before doing so or please do not re-generate this again as this will remove all the modifications made to the resolvers inside this folder, you will be bombartded with errors)
```
sudo go generate graphql/graph/graph.go
```

## update go mod
```
go mod tidy
```

## Build
install all the dependencies from go.mod into vendor folder
```
$ go mod vendor
$ sudo docker-compose up -d --build
```

Open <http://localhost:8000/playground> in your browser.
