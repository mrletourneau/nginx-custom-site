By default this custom `NGINX` docker image behave like a regular stock NGINX image. However, it can be customized in a couple of ways:

- if the `INDEX_HTML_CONTENT` system variable is passed to the container, the image will replace the `index.html` file with the content of the variable
- if the `HTTP_PORT` system variable is passed to the container, the image will configure the `/etc/nginx/conf.d/default.conf` to listen on the port specified in the variable 

A docker image is already available on the docker hub as `mreferre\nginx-custom-site`. 

####Usage 

The command below is equivalent to run the stock nginx docker image:
```
docker run --rm -d -P mreferre/nginx-custom-site:latest
```

The command below runs a stock nginx image replacing the default `index.html` file  with the settings of the `INDEX_HTML_CONTENT` variable and will replace the default port 80 in the `/etc/nginx/conf.d/default.conf` file with port 8080:
```
docker run --rm -d -e INDEX_HTML_CONTENT="My custom web site" -e HTTP_PORT=8080 -p 8080:8080 mreferre/nginx-custom-site:latest
```

The two variables can be used independently. 