Sample for multi environments of docker-compose.yml which be written with DRY
===

[![MIT License](https://img.shields.io/badge/license-MIT-blue.svg?style=flat)](LICENSE)

Requirements
===

* Docker version 17.12.0+
* docker-compose version 1.18.0+

How to startup
===

```bash
$ docker-compose -f proxy.yml -p proxy up -d
$ docker-compose -f docker-compose.yml -f env1.yml -p env1 up -d
$ docker-compose -f docker-compose.yml -f env2.yml -p env2 up -d
```

Test
===

```bash
$ curl -I -H "Host: hoge" localhost
HTTP/1.1 503 Service Temporarily Unavailable
Server: nginx/1.13.9
Date: Sun, 03 Feb 2019 14:03:41 GMT
Content-Type: text/html
Content-Length: 213
Connection: keep-alive
$ curl -H "Host: env1.web.local" localhost
here is env1!
$ curl -H "Host: env1.back.local" localhost
here is env1.back!
$ curl -H "Host: env2.web.local" localhost
here is env2!
$ curl -H "Host: env2.back.local" localhost
here is env2.back!
```

License
===
* [MIT License](LICENSE)

