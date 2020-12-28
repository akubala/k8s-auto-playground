# Automation with Kubernetes - playground

**About**

* Create virtual machine with Vagrant
* Prepare machine for Kubernetes with Ansible
* Deploy simple [micro-blog](https://github.com/akubala/micro-blog) python app with Helm

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
TBD
```

### Destroy cluster

```
vagrant destroy -f
```
