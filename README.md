# resize_disk_scripts
they are fun fun fun,   ubuntu16_lvm works, these were created so that packer can create 9gb starter images and vagrant can use bigger disks, this is the resize bits with fdisk

Break down of all that fdisk stuff. This will delete all partitions past 2 and recreate them bigger, it then forces the partition type of 5 back to LINUX LVM

Then it runs partprobe to tell OS about changes with out reboot, the runs the standard extend disk stuff.

I use this with vagrant as a post shell-provision script, so that I can create mini diskimages with packer, then resize them on 1st boot.
works well for me.


START
==> mail: NR   START      END  SECTORS SIZE NAME UUID
==> mail:  1    2048   999423   997376 487M      18fd3c1f-01
==> mail:  2 1001470 20477951 19476482 9.3G      18fd3c1f-02
==> mail:  5 1001472 20477951 19476480 9.3G      18fd3c1f-05

FINAL result
==> mail: NR   START      END  SECTORS  SIZE NAME UUID
==> mail:  1    2048   999423   997376  487M      18fd3c1f-01
==> mail:  2  999424 67108863 66109440 31.5G      18fd3c1f-02
==> mail:  5 1001472 67108863 66107392 31.5G      18fd3c1f-05

feel free to fork and use


