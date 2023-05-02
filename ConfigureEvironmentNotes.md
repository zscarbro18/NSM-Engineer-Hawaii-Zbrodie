# Configure Notes
---

- In the first terminal type `lxc list`  (this is your container list)
---

- In the second terminal type `ssh elastic@10.81.139.0`    - Replace the 0 in the IP address with the IP on the container list that you are wanting to ssh into.
- Password when getting into ssh is **training**
---
- use command `sudo vi /etc/sysconfig/network-scripts/ifcfg-eth0`
    - When you are in vi, do `:%d` to clear out your vi
    - Copy this into the vi
```
DEVICE=eth0
BOOTPROTO=none
ONBOOT=yes
HOSTNAME=elastic0
NM_CONTROLLED=no
TYPE=Ethernet
IPADDR=10.81.139.28
GATEWAY=10.81.139.1
PREFIX=24
```
- When copied change the HOSTNAME to what network you are using.
- Change your IPADDR to the correct IP that it is supposed to be.
- Get out of insert mode and do `:wq`

---



- Next use command `sudo vi /etc/hosts`
    - When inside vi, do `%d` to clear it out
    - Copy this into vi
```
127.0.0.1 localhost
10.81.139.10 repo
10.81.139.20 sensor
10.81.139.30 elastic0
10.81.139.31 elastic1
10.81.139.32 elastic2
10.81.139.40 pipeline0
10.81.139.41 pipeline1
10.81.139.42 pipeline2
10.81.139.50 kibana
```
- Get out of insert mode and do `:wq`
---
- Do command `sudo systemctl restart network`
---
- On your first terminal run the `lxc list` command to see if the IP has changed.
---
REPEAT FOR ALL NETWORKS!!!