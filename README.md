# go-docker
Docker containers for building go source

Use on OSx to build go executables for alpine, amazon and ubuntu
## Build Container
```
docker-compose pull .
docker-compose build .
docker-compose run --service-ports --rm go-dev
```
## Test Container
```
$ cd src/github.com/user/test
$ go install .
$ test
```
