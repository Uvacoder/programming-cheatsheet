# nginx

## Introduction

[Beginner’s Guide](https://nginx.org/en/docs/beginners_guide.html#conf_structure)

[Exmaple of config files](https://www.nginx.com/resources/wiki/start/topics/examples/full/)

[Reverse Proxy](https://docs.nginx.com/nginx/admin-guide/web-server/reverse-proxy/)

## Questions

## How to overwrite configuration locally from server and user as volumes

[link](https://hub.docker.com/_/nginx) section `Complex configuration`:

```sh
docker run --name tmp-nginx-container -d --rm nginx
docker cp tmp-nginx-container:/etc/nginx/nginx.conf /host/path/nginx.conf
docker run --name tmp-nginx-container -v /host/path/nginx.conf:/etc/nginx/nginx.conf -d nginx
```

Avoid issue with not up docker container because provided volume is empty.

### Jak skierować domenę bezpośrednio na port 8080, bo teraz po uruchomieniu nginx trzeba wpisać w pasku adresu domena.pl:8080

Należy odpalić container przy uzyciu -p ```80:80``` a nie jak to jest w dokumentacji hub docker dla nginx tam znajdziemy tylko: ```8080:8080```

W naszym przypadku będzie to:

```sh
docker run --name some-nginx -d -p 80:80 nginx
```

`-d` flag indicates that we want to run the image in detached mode
`-p` option signifies the port number in the format local-port:container-port
