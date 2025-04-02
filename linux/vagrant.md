#### Install KVM
```
sudo dnf group install -y "virtualization hypervisor"
sudo dnf group install -y "virtualization tools"
sudo systemctl enable --now libvirtd
```

#### Install Vagrant
```
sudo dnf config-manager --add-repo
https://rpm.releases.hashicorp.com/RHEL/hashicorp.repo
sudo dnf install -y vagrant
sudo dnf config-manager --set-enabled crb
sudo dnf install -y libvirt-devel
vagrant plugin install vagrant-libvirt
```

### Add user to libvirt group
```
sudo usermod -aG libvirt YOUR_USERNAME
newgrp
```

#### Quickly provisioning two machines:

```
Vagrant.configure("2") do |config|
  config.vm.box = "generic/rocky9"
  config.vm.provider :libvirt do |libvirt|
    libvirt.memory = 1024
    libvirt.cpus = 2
  end

  config.vm.define "rocky1" do |rocky9_1|
    rocky9_1.vm.hostname = "rocky1"
  end

  config.vm.define "rocky2" do |rocky9_2|
    rocky9_2.vm.hostname = "rocky2"
  end
end

```
