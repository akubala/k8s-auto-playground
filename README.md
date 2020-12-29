# Kubernetes and automation - playground

**About**

* Create virtual machine with Vagrant
* Prepare machine for Kubernetes with Ansible
* Deploy simple [micro-blog](https://github.com/akubala/micro-blog) python app with [Helm chart](https://github.com/akubala/micro-blog-helm-chart)

## Example usage

**Prerequisites**

- Set proper network config in `Vagrantfile`
- Set proper values in `provision/group_vars/all.yml`

### Create cluster

```
vagrant up --provider=virtualbox
```

### Access cluster

```
# Set kubeconfig
export KUBECONFIG="$(pwd)/k8s/.kube/config"

# Show pods info
kubectl get pods --all-namespaces
```

### Play around with micro-blog app

```
# Get data
export POD_NAME=$(kubectl get pods --namespace default -l "app.kubernetes.io/name=micro-blog" -o jsonpath="{.items[0].metadata.name}");
export CONTAINER_PORT=$(kubectl get pod --namespace default $POD_NAME -o jsonpath="{.spec.containers[0].ports[0].containerPort}");

# Visit http://127.0.0.1:8000
kubectl --namespace default port-forward $POD_NAME 8000:$CONTAINER_PORT
```

### Destroy cluster

```
vagrant destroy -f
```
