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

