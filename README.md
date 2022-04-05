# Welcome to the guide!

- This guide is only useful for those with grub at the moment.
- DO NOT USE THIS GUIDE IF YOU DON'T KNOW WHAT YOU'RE DOING, YOU MAY BRICK YOUR LINUX INSTALLATION.

# Dependancies

- cmake
- dracut
- tar
- grub

# Prepare for the installation

make sure you have your ```/boot``` directory properly mounted before proceeding.

wget the kernel version of your choosing...

```https://mirrors.edge.kernel.org/pub/linux/kernel/v5.x/linux-<version>.tar.xz```

prepare the source code files:

```
sudo mkdir /usr/src/linux-<version>
```
```
sudo tar -zxf linux-<version>.tar.gz -C /usr/usr/linux-<version>
```


