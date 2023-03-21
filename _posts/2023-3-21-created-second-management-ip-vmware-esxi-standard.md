# Add Secondary VMkernel Management IP To ESXi Host
## Using the same TCP/IP Stack and vSwitch

1. In the web gui, Create a new port group to use with your new management vmkernel interface. For this example let's call it, "ESXi New MGMT Port Group"

2. SSH into the ESXi host as root 

3. Create a new interface "vmk2" and assign it to the new port group:
```
esxcli network ip interface add -p "ESXi New MGMT Port Group" -i vmk2
```
4. Give the new interface it's IP config. (Remember to change it to your desired IPs)  
```
esxcli network ip interface ipv4 set -i vmk2 -t static -g 192.168.1.1 -I 192.168.1.5 -N 255.255.255.0
```
5. Set or tag the vmkernel for Management
```
esxcli network ip interface tag add -i vmk2 -t Management
```
6. Test


# Sources/Cited Work
- [https://kb.vmware.com/s/article/2010877](https://kb.vmware.com/s/article/2010877)
- [https://learning.oreilly.com/library/view/vmware-vsphere-6-7/9781789953008/d39ecd8d-6410-465e-95c2-88beaa5c9480.xhtml](https://learning.oreilly.com/library/view/vmware-vsphere-6-7/9781789953008/d39ecd8d-6410-465e-95c2-88beaa5c9480.xhtml)
-[https://gainanov.pro/eng-blog/sysad/esxi-cli-networking/](https://gainanov.pro/eng-blog/sysad/esxi-cli-networking/)
