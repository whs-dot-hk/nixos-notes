# Download NixOS
https://channels.nixos.org/nixos-21.11/latest-nixos-gnome-x86_64-linux.iso

![](nixos-download.png "")

# Install NixOS
![](nixos-welcome.png "")
![](nixos-sudo-i.png "")
![](nixos-parted.png "")
![](nixos-parted-all.png "")

```sh
sudo -i
parted /dev/vda -- mklabel gpt
parted /dev/vda -- mkpart primary 512MiB -8GiB
parted /dev/vda -- mkpart primary linux-swap -8GiB 100%
parted /dev/vda -- mkpart ESP fat32 1MiB 512MiB
parted /dev/vda -- set 3 esp on
```

![](nixos-mkfs-ext4.png "")
![](nixos-formatting.png "")
```sh
mkfs.ext4 -L nixos /dev/vda1
mkswap -L swap /dev/vda2
mkfs.fat -F 32 -n boot /dev/vda3
```

![](nixos-mount.png "")
```sh
mkdir -p /mnt/boot
mount /dev/disk/by-label/boot /mnt/boot
swapon /dev/vda2
```

![](nixos-generate-config.png "")
![](nixos-edit-config.png "")
![](nixos-install.png "")
