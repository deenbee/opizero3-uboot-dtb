# Método para actualizar u-boot en la placa de desarrollo opizero3 con 1.5GB de memoria

- Primero descarga el archivo bin de u-boot para 1.5gb de memoria:[1.5gb内存u-boot的bin文件](https://github.com/leeboby/opizero3-uboot-kernel/blob/main/u-boot-sunxi-with-spl-opizero3-1.5gb.bin)
- Luego inserta la tarjeta TF con el sistema linux 6.x grabado para opizero3 en otra máquina linux
- Luego usa el comando sudo fdisk -l para ver el nombre del dispositivo de la tarjeta TF: Por ejemplo: /dev/sdX
- Luego usa el siguiente comando para actualizar el archivo bin de u-boot en la TF:
```
sudo dd bs=1k seek=8 if=u-boot-sunxi-with-spl-opizero3-1.5gb.bin of=/dev/sdX
```

# 4GB内存版本的opizero3开发板更新u-boot和linux内核dtb的方法

- 首先下载4g内存u-boot的bin文件：[4gb内存u-boot的bin文件](https://github.com/leeboby/opizero3-uboot-kernel/blob/main/u-boot-sunxi-with-spl-opizero3-4gb.bin)
- 然后下载4gb内存对应的dtb文件：[4gb内存dtb文件](https://github.com/leeboby/opizero3-uboot-kernel/blob/main/sun50i-h616-orangepi-zero3-4gb.dtb)
- 然后将烧录好opizero3 linux6.x系统的tf卡插入其他的linux机器中
- 然后使用sudo fdisk -l命令查看tf卡的设备名: 比如: /dev/sdX1
- 然后挂载tf卡中的文件系统到linux机器的/mnt目录中：sudo mount /dev/sdX1 /mnt
- 然后将dtb文件复制到tf卡中的 /boot/dtb/allwinner/目录中（这个目录请根据实际情况修改，不要照抄）：
```
sudo cp sun50i-h616-orangepi-zero3-4gb.dtb /mnt/boot/dtb/allwinner/sun50i-h616-orangepi-zero3.dtb
```
- 然后使用下面的命令将u-boot的bin文件更新到tf卡中
```
sudo dd bs=1k seek=8 if=u-boot-sunxi-with-spl-opizero3-4gb.bin of=/dev/sdX
```

