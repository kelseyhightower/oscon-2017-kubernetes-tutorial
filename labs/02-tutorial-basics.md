# Tutorial: Basics

In this tutorial you will walk through running a container with an autoscaling policy and HTTP loadbalancer.

## Deploy Nginx

```
kubectl run nginx --image nginx:1.10
```

```
kubectl get deployments
```

```
kubectl describe deployment nginx
```

```
kubectl get pods
```

Use the describe command to describe the nginx pod created by the nginx deployment:

```
kubectl describe pods <pod-name>
```

## Autoscale

```
kubectl autoscale deployment nginx --cpu-percent=10 --min=2 --max=10
```

```
kubectl get hpa
```

## Expose Nginx

```
kubectl expose deployment nginx --type LoadBalancer --port 80
```

```
kubectl get services
```

```
kubectl describe svc nginx
```

## Troubleshooting

```
kubectl logs 
```

```
kubectl exec --tty -i <pod-name> /bin/sh
```
