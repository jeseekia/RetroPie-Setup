chroot.sh will use qemu (make sure it is installed), to chroot to a raspberry pi system and allow running of
arm binaries etc. the chroot should contain the root filesystem and "boot" also (it checks for boot/kernel.img)

sudo ./chroot.sh DEST COMMAND

COMMAND is optional and will just launch a single command in the chroot.

cleanimage.sh will remove logs/temp files etc from a root filesystem in preparation for making an image for distribution

sudo ./cleanimage.sh DEST

flashsync.sh allows syncing from / to an sdcard/flash device. You can then keep the retropie filesystem on disk, and sync it to a sdcard, and back again if needed. normally managing the data on a pc is fastest and syncing to a flash device just for testing.

sudo ./flashsync.sh from/to DEVICE SOURCE/DEST

eg

sudo ./flashsync from /dev/sde ~/MyRetropie/

will sync the rootfs and the bootfs from /dev/sde1 /dev/sde2 to ~/MyRetropie/ (which can be used for mounting with chroot.sh, cleanimage.sh etc)

makeimage.sh allows creation of images for distribution from a rootfs on hd.

sudo ./makeimage.sh outfile.img path/to/rootfs SIZE

SIZE can be size in BYTES (must be a multiple of 512), "small", or left out for a default (check top of script)

mount.sh mounts an image from sdcard - and is used by flashsync.sh

sudo ./mount.sh /dev/sde /mnt
sudo ./mount.sh umount /mnt
