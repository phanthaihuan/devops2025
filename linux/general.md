#### Disable swap
```
swapoff -a
sysctl vm.swappiness=0
```
Add to the file /etc/sysctl.conf:
```
vm.swappiness=0
```
