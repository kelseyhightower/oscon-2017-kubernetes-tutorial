# Tutorial: Secrets

In this tutorial you will learn how to create and consume Kubernetes secrets.

Create the example application configuration file:

```
cat << EOF > config.json
{
  "username": "admin",
  "password": "123456789"
}
EOF
```

Create the `oscon` secret:

```
kubectl create secret generic oscon \
  --from-literal=username=admin \
  --from-literal=password=123456789 \
  --from-file=config.json
```

Describe the `oscon` secret: 

```
kubectl describe secrets oscon
```

Run the `secrets` job to fetch the secrets and log the secrets:

```
kubectl create -f https://raw.githubusercontent.com/kelseyhightower/secrets/master/secrets.yaml
```

View the logs of the `secrets` job:

```
kubectl get pods -a
```

```
kubectl logs <print-secrets-pod-name>
```

## Managing Secrets with Vault

In this tutorial you will deploy a Vault server running in dev mode.

### Install the vault client on your client machine:

[https://www.vaultproject.io/downloads.html](https://www.vaultproject.io/downloads.html)

### Deploy a Vault Server

```
kubectl create -f https://raw.githubusercontent.com/kelseyhightower/oscon-2017-kubernetes-tutorial/master/statefulsets/vault.yaml
```

```
kubectl get pods
```

```
kubectl get svc
```

```
kubectl logs vault-0
```

### Connect to the Vault Server

```
kubectl port-forward vault-0 8200:8200
```

```
export VAULT_ADDR="http://127.0.0.1:8200"
```

```
export VAULT_TOKEN="3e4a5ba1-oscon-422b-d1db-844979cab098"
```

```
vault status
```


### Add Secrets

```
vault write secret/oscon \
  username=admin \
  password=123456789
```
