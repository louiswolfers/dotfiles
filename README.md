# dotfiles

## Hibernation

src:https://forums.debian.net/viewtopic.php?t=150284

As root:

- [Create a swap file](https://wiki.archlinux.org/title/Swap#Manually)
- Backup grub configuration just in case:

```bash
cp /etc/default/grub  /etc/default/grub.backup
cp /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
```

- Get the offset of the swapfile:

```bash
RESUME_PARAMS="resume=UUID=$(findmnt / -o UUID -n) resume_offset=$(filefrag -v /swapfile|awk 'NR==4{gsub(/\./,"");print $4;}') " && echo $RESUME_PARAMS
vim /etc/default/grub # Change GRUB_CMDLINE_LINUX_DEFAULT="resume=UUID=754a5246-51ba-4890-ac36-9a7b1157f866 resume_offset=2146304"
update-grub
reboot
```
