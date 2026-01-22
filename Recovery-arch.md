recovery

 1. Create efi disk 4G  type Efi system
2. Format to fat 
```
mkfs.vfat -F32 -S 4096 -n BOOT /dev/[path]

```

3. Mount to mnt
```
Mount -o uid=0,gid=0,fmask=0077,dmask=0077 /dev/[path] /mnt
```

4. Mount fd path to opt
```
Mount /dev/[flashdisk] /opt
```
5. Create boot directory
```
mkdir /mnt{efi,loader,kernel}
```
```
mkdir /mnt/efi{linux,boot,recovery,systemd}
```
6. Create boot installer
```
bootctl --path=/mnt install
```
7. Copy installation meidia
```
Cp /opt/arch/boot/x86_64/* /mnt/efi/recovery
```

```
Cp -r /opt/arch/x86_64 /mnt/Efi/recovery
```

8. Create loader file
```
Vim /mnt/loader/entries/recovery.conf
```

Masukan.   Catatan (tab dua kali untuk jarak )


title              recovery
versions       archiso
linux             /efi/recovery/vmlinuz-linux
initrd          /efi/recovery/initramfs-linux.img
options      archisobasedir=efi/recovery archisolabel=BOOT copytoram
