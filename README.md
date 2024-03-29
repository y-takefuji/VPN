# OpenVPN server setup
<pre>
1.find IPv4 address:
 $ dig -4 TXT +short o-o.myaddr.l.google.com @ns1.google.com
2.download an installer, openvpn-install.sh.
 $ wget https://git.io/vpn -O openvpn-install.sh
3.sudo bash openvpn-install.sh
 Protocol [1]: 1 (UDP)
 Port [1194]: 
 DNS server [1]: 2 (Google)
 Name [client]: xxx (name of your device)
 xxx.ovpn file will be created.
4.start VPN server
 $ sudo systemctl start openvpn-server@server.service
5.stop VPN server
 $ sudo systemctl stop openvpn-server@server.service
</pre>

# OpenVPN client setup
<pre>
Linux is a client.
1.install vpn client (linux)
 $ sudo apt install openvpn
2.scp xxx.ovpn client-machine:~
3.download and install client software for your OS:
https://openvpn.net/vpn-client/
4.copy xxx.ovpn to /etc/openvpn/ directory
 $ sudo cp xxx.ovpn /etc/openvpn/client.conf
5.start vpn client
 $ sudo service openvpn start
</pre>
# How to add a new VPN client
$ sudo bash openvpn-install.sh 

# VPN server (PR-500KI) and VPN client (Windows 10) in Japan
<pre>
1. VPN server using PR-500KI router
1.1 click details button, then click vpn server setting
1.2 click edit button, then enter:
server name: VPN
username:  xxx
password: yyy
1.3 click show button to obtain shared key.
you should save the key which will be used for vpn client setting.
1.4 activate vpn setting

VPN client for windows 10
2. On Windows 10, open vpn setting by typing vpn using cortana
2.1. add your vpn setting:
Your vpn server name can be generated by dynamic DNS using freedns.afraid.org. 
Th same username and password are used in vpn client.
name: your vpn server name
server name: your vpn server name
sign-in: username
password: your_password
vpn type: shared key using L2TP/IPsec
shared key: xxxxx
2.2. enter ネットワーク接続 in cortana
right-click your vpn driver and open property.
2.3 pick security type shared-key L2TP/IPsec
2.4 click detail button to enter shared key
2.5 click chap and ms-chap
2.6 click-IPv4 property  and unclick remote network by detail-button
</pre>
