#### Mount disk 
**Get UUID**
```
blkid
```

**Create a mount unit**

```
vi /etc/systemd/system/home.mount
```

Add the following content:

```
[Unit]
Description=Mount /home

[Mount]
What=UUID=a61139c9-6ab3-4f2e-b717-4ed3fb6b8128
Where=/home
Type=auto

[Install]
WantedBy=multi-user.target
```

**Reload systemd**
```
systemctl daemon-reload
```

**Enable and start the mount unit**:
```
systemctl enable home.mount
systemctl start home.mount
```
