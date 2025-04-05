## Mount DVD ISO in Rocky9

Create folder
```
mkdir -p /mnt
```

Locate the ISO file, for example:
```
/home/vagrant/Rocky9.iso
```

Create a mount unit
```
vi /etc/systemd/system/mnt.mount
```

Update the contents:
```
[Unit]
Description=Mount DVD ISO

[Mount]
What=/home/vagrant/Rocky9.iso
Where=/mnt
Type=iso9660
Options=loop

[Install]
WantedBy=multi-user.target
```

Start the service
```
systemctl enable mnt.mount
systemctl start mnt.mount
```

Verify the result
```
lsblk
```
```
NAME               MAJ:MIN RM  SIZE RO TYPE MOUNTPOINTS
loop0                7:0    0 10.7G  0 loop /mnt
vda                252:0    0  128G  0 disk 
├─vda1             252:1    0    1G  0 part /boot
└─vda2             252:2    0  127G  0 part 
  ├─rl_rocky9-root 253:0    0   70G  0 lvm  /
  └─rl_rocky9-swap 253:1    0    2G  0 lvm  [SWAP]
```
The contents of the ISO:
```
[root@rocky1 ~]# ls -lrth /mnt
total 13K
-rw-r--r--. 1 root  root  2.2K Nov  1 03:28 LICENSE
drwxrwxr-x. 1 root  root  2.0K Nov 16 01:52 isolinux
drwxrwxr-x. 1 root  root  2.0K Nov 16 01:52 images
drwxrwxr-x. 1 root  root  2.0K Nov 16 01:52 EFI
-rw-r--r--. 1 root  root   102 Nov 16 03:41 media.repo
drwxr-xr-x. 1 10004 10005 2.0K Nov 16 04:08 AppStream
drwxr-xr-x. 1 10004 10005 2.0K Nov 16 04:09 BaseOS
```

## Configure ISO as local repo
```
vi /etc/yum.repos.d/rocky9.repo
```

```
[BaseOS]
name=BaseOS Packages Rocky Linux 9
metadata_expire=-1
gpgcheck=1
enabled=1
baseurl=file:///mnt/BaseOS/
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release

[AppStream]
name=AppStream Packages Rocky Linux 9
metadata_expire=-1
gpgcheck=1
enabled=1
baseurl=file:///mnt/AppStream/
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release

```

Clean the yum cache:
```
yum clean all
```

List enabled repositories:
```
yum repolist enabled
```

```
[root@rocky1 ~]# yum repolist enabled
repo id                                   repo name
AppStream                                 AppStream Packages Rocky Linux 9
BaseOS                                    BaseOS Packages Rocky Linux 9
appstream                                 Rocky Linux 9 - AppStream
baseos                                    Rocky Linux 9 - BaseOS
epel                                      Extra Packages for Enterprise Linux 9 - x86_64
epel-cisco-openh264                       Extra Packages for Enterprise Linux 9 openh264 (From Cisco) - x86_64
extras                                    Rocky Linux 9 - Extras
```

List the packges from local repositories:
```
dnf --disablerepo="*" --enablerepo="AppStream" list available
dnf --disablerepo="*" --enablerepo="BaseOS" list available
```

Install the packages from the local repositore:
```
dnf --disablerepo="*" --enablerepo="AppStream BaseOS" install tree
```
