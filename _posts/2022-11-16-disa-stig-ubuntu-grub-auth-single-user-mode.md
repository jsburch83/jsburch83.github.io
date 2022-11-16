# After Applying DISA STIG - Ubuntu Asking For Authenication After Reboot 
## Finding ID: V238204
### SV-238204r653787_rule
### Ubuntu operating systems when booted must require authentication upon booting into single-user and maintenance modes.

If you apply the STIG fix for this finding it will cause grub to ask for authenication before booting. Ideally what you want is to only ask when going into single-user and maitenance modes. 

1. Edit this file: /etc/grub.d/10_linux  

Find the line like this: 
```
echo "menuentry '$(echo "$os" | grub_quote)' ${CLASS}
```

2. and change it to this: 
```
echo "menuentry '$(echo "$os" | grub_quote)' --unrestricted ${CLASS}
```

3. Then run 'sudo update-grub'
4. Reboot to see if it will boot like normal. 
5. Also make test and make sure it ask for authenication when trying to boot into recovery mode. 

#Resources:
- https://wiki.archlinux.org/title/Talk:GRUB/Tips_and_tricks#Password_protection_of_non_local_system_boot_options
- https://askubuntu.com/questions/1088215/grub-2-avoid-unrestricted-boot-options-are-overwritten-with-kernel-updates
- https://www.tenable.com/audits/items/DISA_STIG_Ubuntu_16.04_LTS_v2r3.audit:4f894c2e45255b2233084eab8d50abe1 (better STIG fix instructions) 
- https://wiki.archlinux.org/title/GRUB/Tips_and_tricks#Password_protection_of_GRUB_edit_and_console_options_only

