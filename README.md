# SIMPLE CHROOT
## _currently >= ubuntu 18 based supported _

Very opinionate, feel free if you guys need add features.

```
sudo mkdir /mnt/ubuntu
echo init folder success
[ -d /sys/firmware/efi ] && echo “EFI boot on HDD” || echo “Legacy boot on HDD”
echo here wether any information
sudo mount $1 /mnt/ubuntu
sudo mount $1 /mnt/ubuntu/boot/efi
echo mounting root and boot filesystem success
for i in /dev /dev/pts /proc /sys /run; do
	echo detected $i, try to mount em
	sudo mount -B $i /mnt/ubuntu$i
	echo mounting $i succeded
done
echo finally get ready for chroot
sudo chroot /mnt
```
