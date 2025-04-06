## Set timezone
```
timedatectl set-timezone Asia/Ho_Chi_Minh
```

Verify the change:
```
timedatectl show
```
### Chrony
```
dnf -y install chrony
```

```
systemctl status chronyd
```
