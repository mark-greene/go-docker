# go-docker
Docker containers for building go source

Use on OSx to build go executables for alpine, amazon and ubuntu
## Build Container (Dockerfile)
```
docker-compose pull
docker-compose build
```
## Run Container
Maps your local $GOPATH/src folder to container
```
docker-compose run --service-ports --rm go-dev
```
## Test Container
Assumes you have [go-test](https://github.com/mark-greene/go-test) available locally.
```
$ cd src/github.com/mark-greene/go-test/
$ go install .
$ PORT=8080 go-test &
$ wget -O- http://localhost:8080/status
```
## Cleanup
```
$ exit

docker-compose down
```
