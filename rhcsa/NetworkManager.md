## Configure a network profile with NetworkManager

NetworkManager is now managed by GNOME.
(https://networkmanager.dev/)

Configuration files:
(https://docs.rockylinux.org/gemstones/network/RL9_network_manager/)
```
/etc/Network-Manager/system-connections/
/etc/Network-Manager/conf.d/
```

systemd
```
systemctl status NetworkManager
```

Appending IP addresses:
```
nmcli connection modify myprofile1 +ipv4.addresses 172.171.172.172/24
```

Removeing an IP addresses:
```
nmcli connection modify myprofile1 -ipv4.addresses 172.17.172.172/24
```

Reloading the new configuration:
```
nmcli connection reload
```
