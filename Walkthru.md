#Avatar

ssh Aang@127.0.0.1 -p 50500 -L 50501:10.0.0.50:22 -NT
ssh Sokka@ip -L 50500:192.168.1.39(new box):22 -NT
ssh Toph@127.0.0.1 -p 50502 -D 9050 -NT
ssh Katara@127.0.0.1 -p 50501 -L 50502:172.16.1.8:22

Follow along 
nmap port scan from bh to float (22,80)
nc ip 80 to ensure its a web server
port 80 open so run wget -r
review files collected to find creds
ssh Sokka@ip
Host ENUM (ap a, ip route, ip nei, ss -ntlp)
port scan newly found hosts through ip nei with proxychains
proxychains nc discovered open ports
poxychains wget -r
ssh Sokka@ip -L 50500:192.168.1.39(new box):22 -NT
ssh Aang@127.0.0.1 -p 50500
Host ENUM (ap a, ip route, ip nei, ss -ntlp) ip nei | grep -v FAILED(hide failed conections)
ping sweep on Aang ssh term
Close -D and create new 
ssh Aang@127.0.0.1 -p 50500 -D 9050 -NT (on loopback and port bc this is how ssh to aang and now proxychains run on aang)
proxychains nmap port scan
proxychains nc
proxychains wget -r 
ssh Aang@127.0.0.1 -p 50500 -L 50501:10.0.0.50:22 -NT (-L to ssh Katara)
ssh Katara@127.0.0.1 -p 50501 (ssh to katara)
Host ENUM (ap a, ip route, ip nei, ss -ntlp) ip nei | grep -v FAILED(hide failed conections)
ping sweep on Katara ssh term
Close -D and create new 
ssh Katara@127.0.0.1 -p 50501 -D 9050 -NT
proxychains nmap port scan
proxychains nc
proxychains wget -r ip
ssh Katara@127.0.0.1 -p 50501 -L 50502:172.16.1.8:22
ssh Toph@127.0.0.1 -p 50502 (ssh to Toph)
Host ENUM (ap a, ip route, ip nei, ss -ntlp)
Close -D and create new
ssh Toph@127.0.0.1 -p 50502 -D 9050 -NT
port scan newly found hosts through ip nei with proxychains
proxychains nc discovered open ports
poxychains wget -r

Tunnel to get acces to a port you dont have access to or encrypt unencrypted traffic not for ports u have access tooooooo


#Rick&Morty

ssh student@10.50.21.18 -R 50599:127.0.0.1:22 -NT
ssh Beth@127.0.0.1 -p 50502 -D 9050 -NT
ssh Rick@127.0.0.1 -p 50599 -L 50500:10.1.2.18:2222 -NT F to Morty
ssh Morty@127.0.0.1 -p 50500 -L 50501:172.16.10.121:2323 -NT F to Jerry
ssh Jerry@127.0.0.1 -p 50501 -L 50502:192.168.10.69:22 -NT F to Beth

Rick=10.1.2.17 23,80/22int
Morty=10.1.2.18 172.16.10.120 SSH=2222
Jerry=172.16.10.121 SSS=2323
Beth=192.168.10.69 SSH=22

enum host ip for creds from bh with nmap
telnet to Rick with creds
host enum
ping sweep w/ 1 liner
find open ports on rick
ssh student@10.50.21.18 -R 50599:127.0.0.1:22 -NT
ssh Rick@127.0.0.1 -p 50599 -D 9050 -NT
scan follow on networks
find next host and ssh 
ssh Rick@127.0.0.1 -p 50599 -L 50500:10.1.2.18:2222 -NT F to Morty
ssh Morty@127.0.0.1 -p 50500 -D 9050 -NT
host enum
ping sweep w/ 1 liner
find open ports on Morty
scan follow on networks
find next host and ssh port
ssh Morty@127.0.0.1 -p 50500 -L 50501:172.16.10.121:2323 -NT F to Jerry
ssh Jerry@127.0.0.1 -p 50501 -D 9050 -NT
host enum
ping sweep w/ 1 liner
find open ports on Morty
scan follow on networks
find next host and ssh port
ssh Jerry@127.0.0.1 -p 50501 -L 50502:192.168.10.69:22 -NT F to Beth
ssh Beth@127.0.0.1 -p 505002 -D 9050 -NT
host enum
ping sweep w/ 1 liner
find open ports on Morty
scan follow on networks
find next host and ssh port

once -D is the final box execute on flagged port
proxychains nc 127.0.0.1 54321
