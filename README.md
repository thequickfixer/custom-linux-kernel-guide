# Welcome to the guide!

- This guide is only useful for those with grub at the moment.
- DO NOT USE THIS GUIDE IF YOU DON'T KNOW WHAT YOU'RE DOING, YOU MAY BRICK YOUR LINUX INSTALLATION!
- DO NOT DELETE A BACKUP KERNEL! ALWAYS HAVE ONE! MAKE A BACKUP BEFORE ATTEMPTING!
- READ THE LICENSE BEFORE PROCEEDING!
- CONFIRMED WORKING!

# Dependancies

- ```sudo``` / ```doas``` (replace sudo with doas if using doas)
- ```cmake``` (for building)
- ```dracut``` (for initramfs)
- ```zstd``` (to increase compatibility)
- ```tar``` (to extract)
- ```grub``` (required to be installed)
- ```gcc``` (required)

# Prepare for the installation

make sure you have your ```/boot``` directory properly mounted before proceeding (usually it is).

wget the kernel version of your choosing... from the v5.x directory.

```
wget https://mirrors.edge.kernel.org/pub/linux/kernel/v5.x/linux-<version>.tar.xz
```

prepare the source code files:

```
sudo tar -xvf linux-<version>.tar.xz -C /usr/src/
```

# Install patches into linux src manually

Please make sure that the patches are for your specific kernel version (5.15.xx for example) otherwise your kernel will be unable to boot.

To patch the kernel with your specific patches:

```
cd /usr/src/linux-<version>
```

```
sudo patch -p1 < /<directory containing patches>/<yourpatch>.patch
```

# Installation

If you've skipped patching the linux kernel:
```
cd /usr/src/linux-<version>
```

Configure the kernel (Optional but highly recommended):
```
sudo make menuconfig
```

Build the kernel:
```
sudo make -j<number of physical cpu's>
```

Install the modules and install the built kernel:
```
sudo make modules_install && sudo make install
```

# Finishing up the installation

Generate initramfs:
```
sudo dracut --hostonly --force --kver <version>
```

Re-generate the grub-config:
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

# Cleaning up

Remove the kernel tar:
```
sudo rm ~/linux-<version>.tar.xz
```
