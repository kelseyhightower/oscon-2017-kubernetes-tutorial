# Tutorial: Collecting Metrics with Prometheus

In this Tutorial you will walk through installing Prometheus.

## Deploy Prometheus

Download the prometheus configuration file:

```
wget https://raw.githubusercontent.com/kelseyhightower/cloud-native-demo/master/configs/prometheus.yml
```

Create the prometheus configmap:

```
kubectl create configmap prometheus \
  --namespace kube-system \
  --from-file prometheus.yml
```

Create the promethues replicaset:

```
kubectl create -f https://raw.githubusercontent.com/kelseyhightower/cloud-native-demo/master/replicasets/prometheus.yaml
```

```
kubectl get pods -n kube-system
```

Create the prometheus service:

```
kubectl create -f https://raw.githubusercontent.com/kelseyhightower/cloud-native-demo/master/services/prometheus.yaml
```

```
kubectl -n kube-system get pods
```

```
kubectl -n kube-system port-forward <prometheus-pod-name> 9090:9090
```
