
# Disable AUDIT desde Kernel
<details>

<summary>Disable AUDIT desde Kernel</summary>

The change can be implemented the following way:  
1.- Open the file /etc/default/grub  
2.- Append "audit=0" to the space-separated list of options specified in the GRUB_CMDLINE_LINUX_DEFAULT variable.
3.- Save the file
4.- Update the GRUB2 boot loader configuration in /boot/grub2/grub.cfg by executing
`# grub-mkconfig -o /boot/grub/grub.cfg`
5.- Reboot the system
6.- Verify that the setting is present in the /proc/cmdline file

</details>

# Error change version - debian 12

N: Repository 'http://deb.debian.org/debian bookworm InRelease' changed its 'Version' value from '12.6' to '12.7'

apt-get --allow-releaseinfo-change update



# LINUX COMMANDS

alias netl='netstat -an | grep -w LISTEN'
alias sysl='systemctl list-unit-files'



# LINUX COMMANDS

systemctl daemon-reload

systemctl list-unit-files

apt update && apt list --upgradable && apt upgrade && apt autoremove

systemctl stop apparmor && systemctl disable apparmor

lvreduce -L 10G /dev/iac-vg/home -r
lvscan
vgs
lvextend -L 20G /dev/iac-vg/var -r
lvextend -L 20G /dev/iac-vg/root -r

apt install bind9-dnsutils net-tools




# URLs DOCKER INTERESANTES

https://www.virtualizationhowto.com/2024/07/best-docker-container-commands-you-arent-using/



# INSTALL DOCKER

apt-get update
apt-get install sudo ca-certificates curl

install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/debian/gpg -o /etc/apt/keyrings/docker.asc
chmod a+r /etc/apt/keyrings/docker.asc
dpkg --print-architecture
echo   "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/debian \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | tee /etc/apt/sources.list.d/docker.list > /dev/null
cat /etc/apt/sources.list.d/docker.list
apt-get update
apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
docker run hello-world

groupadd docker

usermod -aG docker netalertx
usermod -aG sudo netalertx



# INSTALL prometheus-node-exporter

--collector.processes --no-collector.xfs --no-collector.zfs --no-collector.fibrechannel --no-collector.infiniband --no-collector.nfs --no-collector.nfsd --no-collector.nvme --no-collector.powersupplyclass --no-collector.selinux --collector.tcpstat



# EXECUTE netalertx

docker run -d --network=host   -v /opt/app/config:/app/config   -v /opt/app/db:/app/db   -v /opt/app/log:/app/front/log   -v /opt/app/api:/app/front/api   -e TZ=Europe/Madrid   -e PORT=20211 --name netalertx --restart=always  jokobsk/netalertx:latest


  151  usermod -u 101 netalertx
  152  cat /etc/passwd
  153  vi /etc/passwd
  154  getent group www-data
  155  groupadd -g 82 netalertx
  156  usermod -aG www-data  netalertx




docker run -it -p 3000:3000 --net=host ntop/ntopng:latest -i ens18


iMac Windows 10 (Cable) 98:5a:eb:dd:5d:9a 192.168.1.53
iMac Windows 10 (Wifi) d0:03:4b:ce:d3:71 192.168.1.84

docker run -d --rm --network=host \
  -v /opt/app/config:/app/config \
  -v /opt/app/db:/app/db \
  -v /opt/app/log:/app/front/log \
  -v /opt/app/api:/app/front/api \
  -e TZ=Europe/Madrid \
  -e PORT=20211 \
  jokobsk/netalertx:latest
 
docker run -d --rm --network=host   -v /opt/app/config:/app/config   -v /opt/app/db:/app/db   -v /opt/app/log:/app/front/log   -v /opt/app/api:/app/front/api   -e TZ=Europe/Madrid   -e PORT=20211   jokobsk/netalertx:latest

docker run -d -p 8080:80 -v /opt/dashy/conf.yml:/app/public/conf.yml --name my-dashboard --restart=always lissy93/dashy:latest

docker run -d --name=heimdall -e PUID=1000 -e PGID=1000 -e TZ=Europe/Madrid -p 80:80 -p 443:443 -v /opt/heimdall:/config --restart unless-stopped lscr.io/linuxserver/heimdall:latest

docker run -d --name=Fenrus -e TZ=Europe/Madrid -p 3000:3000 -v /opt/fenrus:/app/data --restart unless-stopped revenz/fenrus:latest

docker run --name homarr --restart unless-stopped -p 7575:7575 -v /var/run/docker.sock:/var/run/docker.sock -v /opt/homarr/configs:/app/data/configs -v /opt/homarr/data:/data -v /opt/homarr/icons:/app/public/icons -d ghcr.io/ajnart/homarr:latest

docker run --pull=always --restart=unless-stopped -d -p 5006:5006 -v /opt/actualbudget:/data --name my_actual_budget actualbudget/actual-server:latest
