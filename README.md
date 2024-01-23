# Método para actualizar u-boot en la placa de desarrollo opizero3 con 1.5GB de memoria

- Primero descarga el archivo bin de u-boot para 1.5gb de memoria:[1.5gb内存u-boot的bin文件](https://github.com/leeboby/opizero3-uboot-kernel/blob/main/u-boot-sunxi-with-spl-opizero3-1.5gb.bin)
- Luego inserta la tarjeta TF con el sistema linux 6.x grabado para opizero3 en otra máquina linux
- Luego usa el comando sudo fdisk -l para ver el nombre del dispositivo de la tarjeta TF: Por ejemplo: /dev/sdX
- Luego usa el siguiente comando para actualizar el archivo bin de u-boot en la TF:
```
sudo dd bs=1k seek=8 if=u-boot-sunxi-with-spl-opizero3-1.5gb.bin of=/dev/sdX
```

# Método para actualizar u-boot y el dtb del kernel linux en la placa opizero3 con 4GB de memoria

- Primero descarga el archivo bin de u-boot para 4gb de memoria：[4gb内存u-boot的bin文件](https://github.com/leeboby/opizero3-uboot-kernel/blob/main/u-boot-sunxi-with-spl-opizero3-4gb.bin)
- Luego descarga el archivo dtb correspondiente a 4gb de memoria：[4gb内存dtb文件](https://github.com/leeboby/opizero3-uboot-kernel/blob/main/sun50i-h616-orangepi-zero3-4gb.dtb)
- Luego inserta la tarjeta TF con el sistema linux 6.x grabado para opizero3 en otra máquina linux
- Luego usa el comando sudo fdisk -l para ver el nombre del dispositivo de la tarjeta TF: Por ejemplo: /dev/sdX1
- Luego monta el sistema de archivos de la TF en el directorio /mnt de la máquina linux: sudo mount /dev/sdX1 /mnt
- Luego copia el archivo dtb en el directorio /boot/dtb/allwinner/ de la TF (modifica este directorio según tu caso, no copies textual):
```
sudo cp sun50i-h616-orangepi-zero3-4gb.dtb /mnt/boot/dtb/allwinner/sun50i-h616-orangepi-zero3.dtb
```
- 然后使用下面的命令将u-boot的bin文件更新到tf卡中
```
sudo dd bs=1k seek=8 if=u-boot-sunxi-with-spl-opizero3-4gb.bin of=/dev/sdX
```

