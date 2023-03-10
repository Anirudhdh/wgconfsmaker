#Debian 10
```echo "deb http://deb.debian.org/debian buster-backports main" >> /etc/apt/sources.list
apt update
apt upgrade
reboot
apt install linux-headers-$(uname -r) wireguard resolvconf qrencode
/usr/sbin/modprobe wireguard
cd /etc/wireguard```

`./mkcerts`
#FILE /etc/ssh/ssh_config +
#	PermitRootLogin yes

FILE /etc/network/interfaces

```auto vdsinavps
iface vdsinavps inet static
        address 10.1.0.3
        netmask 255.255.255.0
        pre-up vdsinavps up $IFACE
        post-down vdsinavps down $IFACE
```

```sysctl -w net.ipv4.ip_forward=1
echo "net.ipv4.ip_forward = 1" >> /etc/sysctl.conf
wg-quick up vdsinavps
systemctl enable wg-quick@vdsinavps.service
systemctl daemon-reload```
