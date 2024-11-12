sudo iptables -L
sudo iptables -L --line-numbers
sudo iptables -A INPUT -p tcp -m multiport --ports 6579,4444 -j ACCEPT
sudo iptables -A INPUT -p udp -m multiport --ports 6579,4444 -j ACCEPT
sudo iptables -A OUTPUT -p udp -m multiport --ports 6579,4444 -j ACCEPT
sudo iptables -A OUTPUT -p tcp -m multiport --ports 6579,4444 -j ACCEPT
sudo iptables -A INPUT -p tcp -m state --state ESTABLISHED,NEW -m multiport --port 22,23,3389,80 -j ACCEPT
sudo iptables -A OUTPUT -p tcp -m state --state ESTABLISHED,NEW -m multiport --port 22,23,3389,80 -j ACCEPT
sudo iptables -D FORWARD 1
sudo iptables -A INPUT -p icmp -s 10.10.0.40 -j ACCEPT
sudo iptables -A OUTPUT -p icmp -d 10.10.0.40 -j ACCEPT
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
sudo iptables -t nat -L --line-numbers




sudo nft list ruleset -ann
sudo nft delete chain ip CCTC handle 2
sudo nft add chain ip CCTC OUTPUT {type filter hook output priority 0 \; policy accept\; }
sudo nft insert rule ip CCTC OUTPUT tcp dport {5050, 5150} accept
sudo nft insert rule ip CCTC INPUT udp dport {5050, 5150} accept
sudo nft insert rule ip CCTC OUTPUT tcp dport {22, 23, 80, 3389} ct state {new, established} accept
sudo nft add chain ip CCTC OUTPUT {\; policy drop\;}
sudo nft add table ip NAT
sudo nft add chain ip NAT PREROUTING {type nat hook prerouting priority 0 \; }
nft add chain ip NAT POSTROUTING {type nat hook postrouting priority 0 \; }
sudo nft add rule ip NAT POSTROUTING ip saddr 192.168.3.30 oif eth0 masquerade















