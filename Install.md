1. Format root
```
mkfs.ext4 -b 4096 /dev/[path]
```
2. Mount root 
```
Mount /Dev/[path] /mnt
```
3. Format data
```
mkfs.ext4 -b 4096 /dev/[path]
```
4. Mount data
```
Mkdir /mnt/home
```
```
Mount /Dev/[path] /mnt
```
5. Install  package
```
pacstrap/mnt linux linux-headers mkinit cpio amd-ucode linux-firmware-amdgpu li nux-firmware-realtek linux-firmware-athe ros linux-firmware-other base base-devel git neovim iwd firewalld iptables-nft aria 2 fuse bash-completion impala wget
```
```
pacman -S hyprland hyprlock xdg-desktop -portal-hyprland hyprpolkitagent hypridle hyprshot gnome-keyring libsecret superfi le perl-image-exiftool lite-xl libnewt uwsm waybar mako wofil brightnessctl cliphist wl-clipboard mpd mpc mpv yt-dlp kitty qt5-wayland qt6-wayland bluez blueman firefox-developer-edition pipewire pipewire-pulse pipewire-jack pipewire-alsa wireplu mber pamixer ttf-jetbrains-mono-nerd ttf-droid ttf-roboto ttf-fira-sans ttf-opensan s btop rocm-smi-lib
```
6. Hostname
```
echo 'nama_user' > etc/hostname
```
```

```
7. Time
```
ln -sf /ust/share/zoneinfo/Asia/Jakarta /etc/localtime
```
```
hwclock --systhoc
```
```
locale-gen
```
8. User
```
useradd -m 'nama_user'
```
```
passwd 'nama_user'
```
```
usermod -aG wheel 'nama_user'
```

uncommenting 
```
nvim /etc/sudoers

uncomenting %wheel ALL=(ALL:ALL) ALL
```
9. Sudoers
```
nvim /etc/sudoers
```
10. Chroot
```
arch-chroot
```
10. Cmdline
```
mkdir /etc/cmdline.d
```
```
touch /etc/cmdline.d/{01-boot.conf,02-mods.conf,03-secs.conf,04-perf.conf,05-nets.conf,06-misc.conf}
```
```
nvim /etc/cmdline.d/01-boot.conf
```
Tambahkan
```
root=/Dev/partisi-root
```
```
nvim /etc/cmdlins.d/06-misc.conf
```
Tambahkan
```
rw quite
```


```
Cd /etc
```
```
Ls
```
Hapus mkinitcpio.conf.d jika ada
```
rm -fr mkinitcpip.conf.d
```
```
mv mkinitcpio.conf mkinitcpip.d/default.conf
```
```
cd mkinitcpio.d
```
```
ls
```
```
nvim Linux.preset
```
![[IMG_20260121_174851_050.jpg]]


Exit
```
cp /etc/systemd/network/* /mnt/etc/systemd/network
```
```
mv intel-ucode.img /mnt/boot/kernel
```

```
Arch-chroot /mnt
```
```
Mkinitcpip -P
```
