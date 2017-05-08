# Create a cluster

In this lab you will create a Kubernetes using the gcloud command.

Set the GCE compute zone:

```
gcloud config set compute/zone us-central1-c
```

Create a Kubernetes cluster named `oscon`:

```
gcloud container clusters create oscon --cluster-version 1.6.2
```
