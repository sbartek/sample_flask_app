## Flask

``` sh
python hello_world_app.py
```

## Docker

``` sh
docker build --tag=helloworldflask .
```

``` sh
docker run --detach --publish=5000:80 --name=helloworldflask helloworldflask
```

Go to <http://localhost:5000/> or run

``` sh
curl http://localhost:5000
```

