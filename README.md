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

### Create deployment for docker container in docker hub

``` sh
kubectl create deployment helloworldflask\
    --image=<username>/helloworldflask:1.0.0
```

#### Alternative: Build docker in minikube environments

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
kubectl run helloworldflask --image=helloworldflask --generator=run-pod/v1
```

Alternative for local docker:
``` sh
kubectl run helloworldflask --image=helloworldflask --image-pull-policy=Never
```

``` sh
kubectl get deployments
```

### Create service

``` sh
kubectl expose deployment helloworldflask --type=LoadBalancer --port=80
```


``` sh
kubectl get services
```


``` sh
minikube service helloworldflask
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

