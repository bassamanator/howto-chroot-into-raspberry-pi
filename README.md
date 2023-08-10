# How to Chroot into a Raspberry Pi MicroSD

## Manjaro Linux As Host (arch based linux distribution)

### Install qemu-user-static-binfmt

```shell
sudo pacman -S qemu-user-static-binfmt
```

#### Restart the service

```sh
sudo systemctl restart systemd-binfmt.service
```

#### Debian install

If you're on a Debian based distribution, install the following packages. The rest of the instructions should be the same, though I can't say for sure.

```shell
sudo apt-get install qemu binfmt-support qemu-user-static
```

### Mount sd card and other locations

```shell
sudo mount /dev/sdX2 /mnt/microsd # Adjust partition
sudo mount --bind /dev /mnt/microsd/dev
sudo mount --bind /proc /mnt/microsd/proc
sudo mount --bind /sys /mnt/microsd/sys
sudo mount --bind /run /mnt/microsd/run
```

### Chroot in

```sh
sudo chroot /mnt/microsd /bin/bash
```

## Unmount everything

```shell
sudo umount /mnt/microsd/dev
sudo umount /mnt/microsd/proc
sudo umount /mnt/microsd/sys
sudo umount /mnt/microsd/run
sudo umount /mnt/microsd
```
