# dotfiles

## Hibernation

src:https://forums.debian.net/viewtopic.php?t=150284

```bash
# cp /etc/default/grub  /etc/default/grub_bak
# cp /boot/grub/grub.cfg /boot/grub/grub.cfg_bak
```

```bash
# RESUME_PARAMS="resume=UUID=$(findmnt / -o UUID -n) resume_offset=$(filefrag -v /swapfile|awk 'NR==4{gsub(/\./,"");print $4;}') " && echo $RESUME_PARAMS
# vim /etc/default/grub # Change GRUB_CMDLINE_LINUX_DEFAULT="resume=UUID=754a5246-51ba-4890-ac36-9a7b1157f866 resume_offset=2146304"
# update-grub
# reboot
```
