## We specify the base image we need for our
## go application
FROM golang:1.12.0-alpine3.9 AS build-env
## We create an /app directory within our
## image that will hold our application source
## files
RUN mkdir /workspace
## We copy everything in the root directory
## into our /app directory
ADD web_project /workspace
## We specify that we now wish to execute 
## any further commands inside our /app
## directory
WORKDIR /workspace
## Add this go mod download command to pull in any dependencies
RUN go mod download
## we run go build to compile the binary
## executable of our Go program
RUN go build -o main .

# Runtime stage
FROM alpine:3.9
WORKDIR /app
COPY --from=build-env /workspace/main /main
## Our start command which kicks off
## our newly created binary executable
CMD ["/main"]
