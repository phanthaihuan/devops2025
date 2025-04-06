## Quick provision RHEL9
(https://portal.cloud.hashicorp.com/vagrant/discover/alvistack/rhel-9)

```
vagrant init alvistack/rhel-9 --box-version 20250403.1.1
```

```
Vagrant.configure("2") do |config|
  config.vm.box = "alvistack/rhel-9"
  config.vm.box_version = "20250403.1.1"
end
```

```
vagrant up
```
