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

## Push to docker hub

``` sh
docker tag helloworldflask <username>/helloworldflask:1.0.0
docker push <username>/helloworldflask:1.0.0
```

This push refers then to repository `docker.io/<username>/helloworldflask`

## k8s with minickube


### Start minikube
``` sh
minikube start
minikube dashboard
```

### Build docker in minikube environments

``` sh
eval $(minikube docker-env)
```

``` sh
docker build --tag=helloworldflask .
```

``` sh
docker images
```

### Run docker

``` sh
kubectl run helloworldapp --image=helloworldapp --image-pull-policy=Never
```

``` sh
kubectl get deployments
```

### Create service

``` sh
kubectl expose deployment helloworldapp --type=LoadBalancer --port=80
```


``` sh
kubectl get services
```


``` sh
minikube service helloworldapp
```

### Clean up

``` sh
kubectl delete service helloworldapp
kubectl delete deployment helloworldapp
minikube stop
minikube delete
```


``` sh
kubectl get pods
```

