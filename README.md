# Welcome to the guide!

- This guide is only useful for those with grub at the moment.
- DO NOT USE THIS GUIDE IF YOU DON'T KNOW WHAT YOU'RE DOING, YOU MAY BRICK YOUR LINUX INSTALLATION!

# Dependancies

- ```sudo``` / ```doas``` (replace sudo with doas if using doas)
- ```cmake``` (for building)
- ```dracut``` (for initramfs)
- ```zstd``` (to increase compatibility)
- ```tar``` (to extract)
- ```grub``` (required to be installed)
- ```gcc``` (required)

# Prepare for the installation

make sure you have your ```/boot``` directory properly mounted before proceeding.

wget the kernel version of your choosing... from the v5.x directory.

```https://mirrors.edge.kernel.org/pub/linux/kernel/v5.x/linux-<version>.tar.xz```

prepare the source code files:

```
sudo mkdir /usr/src/linux-<version>
```
```
sudo tar -zxf linux-<version>.tar.gz -C /usr/src/linux-<version>
```

# Install patches into linux src manually

To patch the kernel with your specific patches:

```
cd /usr/src/linux-<version>
```

```
sudo patch -p1 < /<directory containing patches>/<yourpatch>.patch
```

# Installation

Configure the kernel (Optional but highly recommended):
```
sudo make menuconfig
```

Build the kernel
```
sudo make -j<number of physical cpu's>
```
