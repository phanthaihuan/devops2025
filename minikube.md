#### 1. Add Your User to the KVM Group

```sh
sudo usermod -aG kvm $USER
```

#### 2. Start minikube with 3 nodes
```sh
minikube start --nodes 3
