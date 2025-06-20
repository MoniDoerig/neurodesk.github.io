---
title: "Setup Stratum 1 server"
linkTitle: "Stratum 1"
weight: 1
description: >
  Host a Stratum 1 server
---

The stratum 1 servers for the desktop are configured here: https://github.com/NeuroDesk/neurodesktop/blob/main/Dockerfile

If you want more speed in a region one way could be to setup another Stratum 1 server or a proxy. 

# Setup a Stratum 1 server (This setup works best on Rocky Linux 9):
```bash
sudo yum install -y https://ecsft.cern.ch/dist/cvmfs/cvmfs-release/cvmfs-release-latest.noarch.rpm
sudo yum install -y cvmfs-server squid tmux
sudo yum install -y python3-mod_wsgi 

sudo dnf install dnf-automatic -y
sudo systemctl enable dnf-automatic-install.timer
sudo systemctl status dnf-automatic-install
sudo systemctl cat dnf-automatic-install.timer
sudo vi /etc/dnf/automatic.conf
# check if automatic updates are downloaded and applied

tmux new -s cvmfs
# return to session: tmux a -t cvmfs


sudo sed -i 's/Listen 80/Listen 127.0.0.1:8080/' /etc/httpd/conf/httpd.conf

set +H
echo "http_port 80 accel" | sudo tee /etc/squid/squid.conf
echo "http_port 8000 accel" | sudo tee -a /etc/squid/squid.conf
echo "http_access allow all" | sudo tee -a /etc/squid/squid.conf
echo "cache_peer 127.0.0.1 parent 8080 0 no-query originserver" | sudo tee -a /etc/squid/squid.conf
echo "acl CVMFSAPI urlpath_regex ^/cvmfs/[^/]*/api/" | sudo tee -a /etc/squid/squid.conf
echo "cache deny !CVMFSAPI" | sudo tee -a /etc/squid/squid.conf
echo "cache_mem 128 MB" | sudo tee -a /etc/squid/squid.conf

sudo systemctl start httpd
sudo systemctl start squid
sudo systemctl enable httpd
sudo systemctl enable squid

#YOU NEED TO ADD YOUR GEO IP data here!
echo 'CVMFS_GEO_ACCOUNT_ID=APPLY_FOR_ONE_THIS_IS_a_SIX_DIGIT_NUMBER' | sudo tee -a /etc/cvmfs/server.local
echo 'CVMFS_GEO_LICENSE_KEY=APPLY_FOR_ONE_THIS_IS_a_password' | sudo tee -a /etc/cvmfs/server.local
sudo chmod 600 /etc/cvmfs/server.local

sudo mkdir -p /etc/cvmfs/keys/ardc.edu.au/

echo "-----BEGIN PUBLIC KEY-----
MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAwUPEmxDp217SAtZxaBep
Bi2TQcLoh5AJ//HSIz68ypjOGFjwExGlHb95Frhu1SpcH5OASbV+jJ60oEBLi3sD
qA6rGYt9kVi90lWvEjQnhBkPb0uWcp1gNqQAUocybCzHvoiG3fUzAe259CrK09qR
pX8sZhgK3eHlfx4ycyMiIQeg66AHlgVCJ2fKa6fl1vnh6adJEPULmn6vZnevvUke
I6U1VcYTKm5dPMrOlY/fGimKlyWvivzVv1laa5TAR2Dt4CfdQncOz+rkXmWjLjkD
87WMiTgtKybsmMLb2yCGSgLSArlSWhbMA0MaZSzAwE9PJKCCMvTANo5644zc8jBe
NQIDAQAB
-----END PUBLIC KEY-----" | sudo tee /etc/cvmfs/keys/ardc.edu.au/neurodesk.ardc.edu.au.pub


sudo cvmfs_server add-replica -o $USER http://stratum0.neurodesk.cloud.edu.au/cvmfs/neurodesk.ardc.edu.au /etc/cvmfs/keys/ardc.edu.au

# CVMFS will store everything in /srv/cvmfs so make sure there is enough space or create a symlink to a bigger storage volume
# e.g.:
#cd /storage
#sudo mkdir -p cvmfs-storage/srv/
#cd /srv/
#sudo mv cvmfs/ /storage/cvmfs-storage/srv/
#sudo ln -s /storage/cvmfs-storage/srv/cvmfs/ -->


sudo cvmfs_server snapshot neurodesk.ardc.edu.au


echo "/var/log/cvmfs/*.log {
    weekly
    missingok
    notifempty
}" | sudo tee /etc/logrotate.d/cvmfs


echo '*/5 * * * * root output=$(/usr/bin/cvmfs_server snapshot -a -i 2>&1) || echo "$output" ' | sudo tee /etc/cron.d/cvmfs_stratum1_snapshot

sudo yum install iptables
sudo iptables -t nat -A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8000

sudo systemctl disable firewalld 
sudo systemctl stop firewalld 
# make sure that port 80 is open in the real firewall

sudo cvmfs_server update-geodb

#test
curl --head http://YOUR_IP_OR_DNS/cvmfs/neurodesk.ardc.edu.au/.cvmfspublished

```
