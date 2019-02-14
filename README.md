Hello World
===========

This is a simple image that just gives a response on port 8000. Use this to
test your web orchestration. It's small enough to fit on one floppy disk:

```bash
$ docker images | grep hell
REPOSITORY               TAG       IMAGE ID        CREATED          VIRTUAL SIZE
tomma/helloworld     latest    2b28c6ad8d1b        3 hours     1.13MB
```


Sample Usage
------------

### Starting a web server on port 80

```bash
$ docker run -d --name web-test -p 80:8000 tomma/helloworld
```

You can now interact with this as if it were a dumb web server:
```
$ curl localhost
Hello World
...

# Every request returns the same thing
$ curl -X POST localhost/super/secret
Hello World
...

# Does not send actual HTTP responses (this should probably change so this can
# be used with load balancers)
$ curl --write-out %{http_code} --silent --output /dev/null localhost
000
```
