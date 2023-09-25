Recover the imported virtual machine from the emergency mode

    In emergency mode, enter the root password of the virtual machine.
    Enter the command below to delete the original device file.
    [root@localhost ~]# rm /etc/lvm/devices/system.devices
    Enter the command below to create a new device file.
    [root@localhost ~]# vgimportdevices -a
    Enter the command below to reboot the virtual machine.
    [root@localhost ~]# reboot
