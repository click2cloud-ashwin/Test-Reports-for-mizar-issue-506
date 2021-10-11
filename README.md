# Test report for deploying Application pods on Arktos cluster with Mizar as CNI on GCP

This document captures the steps to deploy an Arktos cluster lab with mizar cni. The machines in this lab used are n2-custom-16-32768 (16 CPUs, 32GB mem), Ubuntu 18.04 LTS.

**Date**: 11.10.2021
### Create an instance on GCP
Created instance on GCP

![image](https://user-images.githubusercontent.com/82659622/136737232-60512522-fbf0-420b-a459-4e3531a1f48a.png)


### Step-1: Update kernel version

* Check kernel version:
```bash
uname -a
```
##### Output
````bigquery
Linux tesseract 4.15.0-1098-gcp #111~16.04.1-Ubuntu SMP Tue Apr 13 19:05:08 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
````

Here kernel version was `4.15.0-1098-gcp` hence, to update kernel version to `5.6.0-rc2`, we used following steps :

```bash
wget https://raw.githubusercontent.com/CentaurusInfra/mizar/dev-next/kernelupdate.sh
sudo bash kernelupdate.sh
```

##### Output
```bigquery
root@tesseract:~# sudo bash kernelupdate.sh
--2021-10-11 05:23:05--  https://mizar.s3.amazonaws.com/linux-5.6-rc2/linux-headers-5.6.0-rc2_5.6.0-rc2-1_amd64.deb
Resolving mizar.s3.amazonaws.com (mizar.s3.amazonaws.com)... 52.217.173.153
Connecting to mizar.s3.amazonaws.com (mizar.s3.amazonaws.com)|52.217.173.153|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 7621020 (7.3M) []
Saving to: ‘../linux-5.6-rc2/linux-headers-5.6.0-rc2_5.6.0-rc2-1_amd64.deb’

linux-headers-5.6.0-rc2_5.6.0-rc2-1_amd64. 100%[=======================================================================================>]   7.27M  12.1MB/s    in 0.6s

2021-10-11 05:23:06 (12.1 MB/s) - ‘../linux-5.6-rc2/linux-headers-5.6.0-rc2_5.6.0-rc2-1_amd64.deb’ saved [7621020/7621020]

--2021-10-11 05:23:06--  https://mizar.s3.amazonaws.com/linux-5.6-rc2/linux-image-5.6.0-rc2-dbg_5.6.0-rc2-1_amd64.deb
Resolving mizar.s3.amazonaws.com (mizar.s3.amazonaws.com)... 52.217.173.153
Connecting to mizar.s3.amazonaws.com (mizar.s3.amazonaws.com)|52.217.173.153|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 857827912 (818M) [application/x-www-form-urlencoded]
Saving to: ‘../linux-5.6-rc2/linux-image-5.6.0-rc2-dbg_5.6.0-rc2-1_amd64.deb’

linux-image-5.6.0-rc2-dbg_5.6.0-rc2-1_amd64.deb  100%[=======================================================================================================>] 818.09M  44.5MB/s    in 19s

2021-10-11 05:23:26 (42.0 MB/s) - ‘../linux-5.6-rc2/linux-image-5.6.0-rc2-dbg_5.6.0-rc2-1_amd64.deb’ saved [857827912/857827912]

--2021-10-11 05:23:26--  https://mizar.s3.amazonaws.com/linux-5.6-rc2/linux-image-5.6.0-rc2_5.6.0-rc2-1_amd64.deb
Resolving mizar.s3.amazonaws.com (mizar.s3.amazonaws.com)... 52.216.92.203
Connecting to mizar.s3.amazonaws.com (mizar.s3.amazonaws.com)|52.216.92.203|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 56427036 (54M) [application/x-www-form-urlencoded]
Saving to: ‘../linux-5.6-rc2/linux-image-5.6.0-rc2_5.6.0-rc2-1_amd64.deb’

linux-image-5.6.0-rc2_5.6.0-rc2-1_amd64.deb      100%[=======================================================================================================>]  53.81M  29.4MB/s    in 1.8s

2021-10-11 05:23:28 (29.4 MB/s) - ‘../linux-5.6-rc2/linux-image-5.6.0-rc2_5.6.0-rc2-1_amd64.deb’ saved [56427036/56427036]

--2021-10-11 05:23:28--  https://mizar.s3.amazonaws.com/linux-5.6-rc2/linux-libc-dev_5.6.0-rc2-1_amd64.deb
Resolving mizar.s3.amazonaws.com (mizar.s3.amazonaws.com)... 52.216.92.203
Connecting to mizar.s3.amazonaws.com (mizar.s3.amazonaws.com)|52.216.92.203|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1082248 (1.0M) []
Saving to: ‘../linux-5.6-rc2/linux-libc-dev_5.6.0-rc2-1_amd64.deb’

linux-libc-dev_5.6.0-rc2-1_amd64.deb             100%[=======================================================================================================>]   1.03M  2.59MB/s    in 0.4s

2021-10-11 05:23:29 (2.59 MB/s) - ‘../linux-5.6-rc2/linux-libc-dev_5.6.0-rc2-1_amd64.deb’ saved [1082248/1082248]

Continue kernel update (y/n)?y
Updating kernel
Selecting previously unselected package linux-headers-5.6.0-rc2.
(Reading database ... 57240 files and directories currently installed.)
Preparing to unpack .../linux-headers-5.6.0-rc2_5.6.0-rc2-1_amd64.deb ...
Unpacking linux-headers-5.6.0-rc2 (5.6.0-rc2-1) ...
Selecting previously unselected package linux-image-5.6.0-rc2-dbg.
Preparing to unpack .../linux-image-5.6.0-rc2-dbg_5.6.0-rc2-1_amd64.deb ...
Unpacking linux-image-5.6.0-rc2-dbg (5.6.0-rc2-1) ...
Selecting previously unselected package linux-image-5.6.0-rc2.
Preparing to unpack .../linux-image-5.6.0-rc2_5.6.0-rc2-1_amd64.deb ...
Unpacking linux-image-5.6.0-rc2 (5.6.0-rc2-1) ...
Selecting previously unselected package linux-libc-dev:amd64.
Preparing to unpack .../linux-libc-dev_5.6.0-rc2-1_amd64.deb ...
Unpacking linux-libc-dev:amd64 (5.6.0-rc2-1) ...
Setting up linux-headers-5.6.0-rc2 (5.6.0-rc2-1) ...
Setting up linux-image-5.6.0-rc2-dbg (5.6.0-rc2-1) ...
Setting up linux-image-5.6.0-rc2 (5.6.0-rc2-1) ...
update-initramfs: Generating /boot/initrd.img-5.6.0-rc2
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/50-cloudimg-settings.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.6.0-rc2
Found initrd image: /boot/initrd.img-5.6.0-rc2
Found linux image: /boot/vmlinuz-5.4.0-1045-aws
Found initrd image: /boot/initrd.img-5.4.0-1045-aws
done
Setting up linux-libc-dev:amd64 (5.6.0-rc2-1) ...
Reboot host (y/n)?y
Rebooting
```

### Step-2:Install dependencies
Login to created instance and run following steps to install dependencies required for arktos deployment:

* Clone the Arktos repository
```bash
git clone https://github.com/CentaurusInfra/arktos.git ~/go/src/k8s.io/arktos 
```
##### Output
```bigquery
root@tesseract:~# git clone https://github.com/CentaurusInfra/arktos.git ~/go/src/k8s.io/arktos
Cloning into '/home/ubuntu/go/src/k8s.io/arktos'...
remote: Enumerating objects: 104938, done.
remote: Counting objects: 100% (447/447), done.
remote: Compressing objects: 100% (258/258), done.
remote: Total 104938 (delta 209), reused 341 (delta 173), pack-reused 104491
Receiving objects: 100% (104938/104938), 227.98 MiB | 25.72 MiB/s, done.
Resolving deltas: 100% (63446/63446), done.
Checking out files: 100% (20757/20757), done.
```

Then installed prerequisites required for Arktos cluster using following command
```
sudo bash $HOME/go/src/k8s.io/arktos/hack/setup-dev-node.sh
```
##### Output
```bigquery
root@tesseract:~# sudo bash $HOME/go/src/k8s.io/arktos/hack/setup-dev-node.sh
The script is to help install prerequisites of Arktos development environment
on a fresh Linux installation.
It's been tested on Ubuntu 16.04 LTS and 18.04 LTS.
Update apt.
Hit:1 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic InRelease
Hit:2 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic-updates InRelease
Hit:3 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic-backports InRelease
Get:4 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]
Fetched 88.7 kB in 0s (238 kB/s)
Reading package lists... Done
Building dependency tree
Reading state information... Done
All packages are up to date.
Install docker.
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following package was automatically installed and is no longer required:
  libnuma1
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  bridge-utils containerd pigz runc ubuntu-fan
Suggested packages:
  ifupdown aufs-tools cgroupfs-mount | cgroup-lite debootstrap docker-doc rinse zfs-fuse | zfsutils
The following NEW packages will be installed:
  bridge-utils containerd docker.io pigz runc ubuntu-fan
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 74.0 MB of archives.
After this operation, 359 MB of additional disk space will be used.
Get:1 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic/universe amd64 pigz amd64 2.4-1 [57.4 kB]
Get:2 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic/main amd64 bridge-utils amd64 1.5-15ubuntu1 [30.1 kB]
Get:3 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 runc amd64 1.0.0~rc95-0ubuntu1~18.04.2 [4087 kB]
Get:4 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 containerd amd64 1.5.2-0ubuntu1~18.04.3 [32.8 MB]
Get:5 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 docker.io amd64 20.10.7-0ubuntu1~18.04.2 [36.9 MB]
Get:6 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic/main amd64 ubuntu-fan all 0.12.10 [34.7 kB]
Fetched 74.0 MB in 1s (59.0 MB/s)
Preconfiguring packages ...
Selecting previously unselected package pigz.
(Reading database ... 97215 files and directories currently installed.)
Preparing to unpack .../0-pigz_2.4-1_amd64.deb ...
Unpacking pigz (2.4-1) ...
Selecting previously unselected package bridge-utils.
Preparing to unpack .../1-bridge-utils_1.5-15ubuntu1_amd64.deb ...
Unpacking bridge-utils (1.5-15ubuntu1) ...
Selecting previously unselected package runc.
Preparing to unpack .../2-runc_1.0.0~rc95-0ubuntu1~18.04.2_amd64.deb ...
Unpacking runc (1.0.0~rc95-0ubuntu1~18.04.2) ...
Selecting previously unselected package containerd.
Preparing to unpack .../3-containerd_1.5.2-0ubuntu1~18.04.3_amd64.deb ...
Unpacking containerd (1.5.2-0ubuntu1~18.04.3) ...
Selecting previously unselected package docker.io.
Preparing to unpack .../4-docker.io_20.10.7-0ubuntu1~18.04.2_amd64.deb ...
Unpacking docker.io (20.10.7-0ubuntu1~18.04.2) ...
Selecting previously unselected package ubuntu-fan.
Preparing to unpack .../5-ubuntu-fan_0.12.10_all.deb ...
Unpacking ubuntu-fan (0.12.10) ...
Setting up runc (1.0.0~rc95-0ubuntu1~18.04.2) ...
Setting up containerd (1.5.2-0ubuntu1~18.04.3) ...
Created symlink /etc/systemd/system/multi-user.target.wants/containerd.service → /lib/systemd/system/containerd.service.
Setting up bridge-utils (1.5-15ubuntu1) ...
Setting up ubuntu-fan (0.12.10) ...
Created symlink /etc/systemd/system/multi-user.target.wants/ubuntu-fan.service → /lib/systemd/system/ubuntu-fan.service.
Setting up pigz (2.4-1) ...
Setting up docker.io (20.10.7-0ubuntu1~18.04.2) ...
Adding group `docker' (GID 116) ...
Done.
Created symlink /etc/systemd/system/multi-user.target.wants/docker.service → /lib/systemd/system/docker.service.
Created symlink /etc/systemd/system/sockets.target.wants/docker.socket → /lib/systemd/system/docker.socket.
Processing triggers for systemd (237-3ubuntu10.52) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for ureadahead (0.100.0-21) ...
Install make & gcc.
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following package was automatically installed and is no longer required:
  libnuma1
Use 'sudo apt autoremove' to remove it.
Suggested packages:
  make-doc
The following NEW packages will be installed:
  make
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 154 kB of archives.
After this operation, 381 kB of additional disk space will be used.
Get:1 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic/main amd64 make amd64 4.1-9.1ubuntu1 [154 kB]
Fetched 154 kB in 0s (0 B/s)
Selecting previously unselected package make.
(Reading database ... 97537 files and directories currently installed.)
Preparing to unpack .../make_4.1-9.1ubuntu1_amd64.deb ...
Unpacking make (4.1-9.1ubuntu1) ...
Setting up make (4.1-9.1ubuntu1) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following package was automatically installed and is no longer required:
  libnuma1
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  binutils binutils-common binutils-x86-64-linux-gnu cpp cpp-7 gcc-7 gcc-7-base libasan4 libatomic1 libbinutils libc-dev-bin libc6-dev libcc1-0 libcilkrts5 libgcc-7-dev libgomp1 libisl19
  libitm1 liblsan0 libmpc3 libmpx2 libquadmath0 libtsan0 libubsan0 manpages-dev
Suggested packages:
  binutils-doc cpp-doc gcc-7-locales gcc-multilib autoconf automake libtool flex bison gdb gcc-doc gcc-7-multilib gcc-7-doc libgcc1-dbg libgomp1-dbg libitm1-dbg libatomic1-dbg libasan4-dbg
  liblsan0-dbg libtsan0-dbg libubsan0-dbg libcilkrts5-dbg libmpx2-dbg libquadmath0-dbg glibc-doc
The following NEW packages will be installed:
  binutils binutils-common binutils-x86-64-linux-gnu cpp cpp-7 gcc gcc-7 gcc-7-base libasan4 libatomic1 libbinutils libc-dev-bin libc6-dev libcc1-0 libcilkrts5 libgcc-7-dev libgomp1 libisl19
  libitm1 liblsan0 libmpc3 libmpx2 libquadmath0 libtsan0 libubsan0 manpages-dev
0 upgraded, 26 newly installed, 0 to remove and 0 not upgraded.
Need to get 29.6 MB of archives.
After this operation, 112 MB of additional disk space will be used.
Get:1 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic-updates/main amd64 binutils-common amd64 2.30-21ubuntu1~18.04.5 [197 kB]
Get:2 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libbinutils amd64 2.30-21ubuntu1~18.04.5 [489 kB]
Get:3 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic-updates/main amd64 binutils-x86-64-linux-gnu amd64 2.30-21ubuntu1~18.04.5 [1839 kB]
Get:4 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic-updates/main amd64 binutils amd64 2.30-21ubuntu1~18.04.5 [3388 B]
Get:5 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic-updates/main amd64 gcc-7-base amd64 7.5.0-3ubuntu1~18.04 [18.3 kB]
Get:6 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic/main amd64 libisl19 amd64 0.19-1 [551 kB]
Get:7 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic/main amd64 libmpc3 amd64 1.1.0-1 [40.8 kB]
Get:8 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic-updates/main amd64 cpp-7 amd64 7.5.0-3ubuntu1~18.04 [8591 kB]
Get:9 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic-updates/main amd64 cpp amd64 4:7.4.0-1ubuntu2.3 [27.7 kB]
Get:10 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libcc1-0 amd64 8.4.0-1ubuntu1~18.04 [39.4 kB]
Get:11 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libgomp1 amd64 8.4.0-1ubuntu1~18.04 [76.5 kB]
Get:12 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libitm1 amd64 8.4.0-1ubuntu1~18.04 [27.9 kB]
Get:13 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libatomic1 amd64 8.4.0-1ubuntu1~18.04 [9192 B]
Get:14 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libasan4 amd64 7.5.0-3ubuntu1~18.04 [358 kB]
Get:15 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic-updates/main amd64 liblsan0 amd64 8.4.0-1ubuntu1~18.04 [133 kB]
Get:16 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libtsan0 amd64 8.4.0-1ubuntu1~18.04 [288 kB]
Get:17 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libubsan0 amd64 7.5.0-3ubuntu1~18.04 [126 kB]
Get:18 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libcilkrts5 amd64 7.5.0-3ubuntu1~18.04 [42.5 kB]
Get:19 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libmpx2 amd64 8.4.0-1ubuntu1~18.04 [11.6 kB]
Get:20 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libquadmath0 amd64 8.4.0-1ubuntu1~18.04 [134 kB]
Get:21 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libgcc-7-dev amd64 7.5.0-3ubuntu1~18.04 [2378 kB]
Get:22 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic-updates/main amd64 gcc-7 amd64 7.5.0-3ubuntu1~18.04 [9381 kB]
Get:23 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic-updates/main amd64 gcc amd64 4:7.4.0-1ubuntu2.3 [5184 B]
Get:24 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libc-dev-bin amd64 2.27-3ubuntu1.4 [71.8 kB]
Get:25 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libc6-dev amd64 2.27-3ubuntu1.4 [2585 kB]
Get:26 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic/main amd64 manpages-dev all 4.15-1 [2217 kB]
Fetched 29.6 MB in 0s (79.4 MB/s)
Selecting previously unselected package binutils-common:amd64.
(Reading database ... 97553 files and directories currently installed.)
Preparing to unpack .../00-binutils-common_2.30-21ubuntu1~18.04.5_amd64.deb ...
Unpacking binutils-common:amd64 (2.30-21ubuntu1~18.04.5) ...
Selecting previously unselected package libbinutils:amd64.
Preparing to unpack .../01-libbinutils_2.30-21ubuntu1~18.04.5_amd64.deb ...
Unpacking libbinutils:amd64 (2.30-21ubuntu1~18.04.5) ...
Selecting previously unselected package binutils-x86-64-linux-gnu.
Preparing to unpack .../02-binutils-x86-64-linux-gnu_2.30-21ubuntu1~18.04.5_amd64.deb ...
Unpacking binutils-x86-64-linux-gnu (2.30-21ubuntu1~18.04.5) ...
Selecting previously unselected package binutils.
Preparing to unpack .../03-binutils_2.30-21ubuntu1~18.04.5_amd64.deb ...
Unpacking binutils (2.30-21ubuntu1~18.04.5) ...
Selecting previously unselected package gcc-7-base:amd64.
Preparing to unpack .../04-gcc-7-base_7.5.0-3ubuntu1~18.04_amd64.deb ...
Unpacking gcc-7-base:amd64 (7.5.0-3ubuntu1~18.04) ...
Selecting previously unselected package libisl19:amd64.
Preparing to unpack .../05-libisl19_0.19-1_amd64.deb ...
Unpacking libisl19:amd64 (0.19-1) ...
Selecting previously unselected package libmpc3:amd64.
Preparing to unpack .../06-libmpc3_1.1.0-1_amd64.deb ...
Unpacking libmpc3:amd64 (1.1.0-1) ...
Selecting previously unselected package cpp-7.
Preparing to unpack .../07-cpp-7_7.5.0-3ubuntu1~18.04_amd64.deb ...
Unpacking cpp-7 (7.5.0-3ubuntu1~18.04) ...
Selecting previously unselected package cpp.
Preparing to unpack .../08-cpp_4%3a7.4.0-1ubuntu2.3_amd64.deb ...
Unpacking cpp (4:7.4.0-1ubuntu2.3) ...
Selecting previously unselected package libcc1-0:amd64.
Preparing to unpack .../09-libcc1-0_8.4.0-1ubuntu1~18.04_amd64.deb ...
Unpacking libcc1-0:amd64 (8.4.0-1ubuntu1~18.04) ...
Selecting previously unselected package libgomp1:amd64.
Preparing to unpack .../10-libgomp1_8.4.0-1ubuntu1~18.04_amd64.deb ...
Unpacking libgomp1:amd64 (8.4.0-1ubuntu1~18.04) ...
Selecting previously unselected package libitm1:amd64.
Preparing to unpack .../11-libitm1_8.4.0-1ubuntu1~18.04_amd64.deb ...
Unpacking libitm1:amd64 (8.4.0-1ubuntu1~18.04) ...
Selecting previously unselected package libatomic1:amd64.
Preparing to unpack .../12-libatomic1_8.4.0-1ubuntu1~18.04_amd64.deb ...
Unpacking libatomic1:amd64 (8.4.0-1ubuntu1~18.04) ...
Selecting previously unselected package libasan4:amd64.
Preparing to unpack .../13-libasan4_7.5.0-3ubuntu1~18.04_amd64.deb ...
Unpacking libasan4:amd64 (7.5.0-3ubuntu1~18.04) ...
Selecting previously unselected package liblsan0:amd64.
Preparing to unpack .../14-liblsan0_8.4.0-1ubuntu1~18.04_amd64.deb ...
Unpacking liblsan0:amd64 (8.4.0-1ubuntu1~18.04) ...
Selecting previously unselected package libtsan0:amd64.
Preparing to unpack .../15-libtsan0_8.4.0-1ubuntu1~18.04_amd64.deb ...
Unpacking libtsan0:amd64 (8.4.0-1ubuntu1~18.04) ...
Selecting previously unselected package libubsan0:amd64.
Preparing to unpack .../16-libubsan0_7.5.0-3ubuntu1~18.04_amd64.deb ...
Unpacking libubsan0:amd64 (7.5.0-3ubuntu1~18.04) ...
Selecting previously unselected package libcilkrts5:amd64.
Preparing to unpack .../17-libcilkrts5_7.5.0-3ubuntu1~18.04_amd64.deb ...
Unpacking libcilkrts5:amd64 (7.5.0-3ubuntu1~18.04) ...
Selecting previously unselected package libmpx2:amd64.
Preparing to unpack .../18-libmpx2_8.4.0-1ubuntu1~18.04_amd64.deb ...
Unpacking libmpx2:amd64 (8.4.0-1ubuntu1~18.04) ...
Selecting previously unselected package libquadmath0:amd64.
Preparing to unpack .../19-libquadmath0_8.4.0-1ubuntu1~18.04_amd64.deb ...
Unpacking libquadmath0:amd64 (8.4.0-1ubuntu1~18.04) ...
Selecting previously unselected package libgcc-7-dev:amd64.
Preparing to unpack .../20-libgcc-7-dev_7.5.0-3ubuntu1~18.04_amd64.deb ...
Unpacking libgcc-7-dev:amd64 (7.5.0-3ubuntu1~18.04) ...
Selecting previously unselected package gcc-7.
Preparing to unpack .../21-gcc-7_7.5.0-3ubuntu1~18.04_amd64.deb ...
Unpacking gcc-7 (7.5.0-3ubuntu1~18.04) ...
Selecting previously unselected package gcc.
Preparing to unpack .../22-gcc_4%3a7.4.0-1ubuntu2.3_amd64.deb ...
Unpacking gcc (4:7.4.0-1ubuntu2.3) ...
Selecting previously unselected package libc-dev-bin.
Preparing to unpack .../23-libc-dev-bin_2.27-3ubuntu1.4_amd64.deb ...
Unpacking libc-dev-bin (2.27-3ubuntu1.4) ...
Selecting previously unselected package libc6-dev:amd64.
Preparing to unpack .../24-libc6-dev_2.27-3ubuntu1.4_amd64.deb ...
Unpacking libc6-dev:amd64 (2.27-3ubuntu1.4) ...
Selecting previously unselected package manpages-dev.
Preparing to unpack .../25-manpages-dev_4.15-1_all.deb ...
Unpacking manpages-dev (4.15-1) ...
Setting up libquadmath0:amd64 (8.4.0-1ubuntu1~18.04) ...
Setting up libgomp1:amd64 (8.4.0-1ubuntu1~18.04) ...
Setting up libatomic1:amd64 (8.4.0-1ubuntu1~18.04) ...
Setting up libcc1-0:amd64 (8.4.0-1ubuntu1~18.04) ...
Setting up libtsan0:amd64 (8.4.0-1ubuntu1~18.04) ...
Setting up liblsan0:amd64 (8.4.0-1ubuntu1~18.04) ...
Setting up gcc-7-base:amd64 (7.5.0-3ubuntu1~18.04) ...
Setting up binutils-common:amd64 (2.30-21ubuntu1~18.04.5) ...
Setting up libmpx2:amd64 (8.4.0-1ubuntu1~18.04) ...
Setting up libmpc3:amd64 (1.1.0-1) ...
Setting up libc-dev-bin (2.27-3ubuntu1.4) ...
Setting up manpages-dev (4.15-1) ...
Setting up libc6-dev:amd64 (2.27-3ubuntu1.4) ...
Setting up libitm1:amd64 (8.4.0-1ubuntu1~18.04) ...
Setting up libisl19:amd64 (0.19-1) ...
Setting up libasan4:amd64 (7.5.0-3ubuntu1~18.04) ...
Setting up libbinutils:amd64 (2.30-21ubuntu1~18.04.5) ...
Setting up libcilkrts5:amd64 (7.5.0-3ubuntu1~18.04) ...
Setting up libubsan0:amd64 (7.5.0-3ubuntu1~18.04) ...
Setting up libgcc-7-dev:amd64 (7.5.0-3ubuntu1~18.04) ...
Setting up cpp-7 (7.5.0-3ubuntu1~18.04) ...
Setting up binutils-x86-64-linux-gnu (2.30-21ubuntu1~18.04.5) ...
Setting up cpp (4:7.4.0-1ubuntu2.3) ...
Setting up binutils (2.30-21ubuntu1~18.04.5) ...
Setting up gcc-7 (7.5.0-3ubuntu1~18.04) ...
Setting up gcc (4:7.4.0-1ubuntu2.3) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for libc-bin (2.27-3ubuntu1.4) ...
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following package was automatically installed and is no longer required:
  libnuma1
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  libjq1 libonig4
The following NEW packages will be installed:
  jq libjq1 libonig4
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 276 kB of archives.
After this operation, 930 kB of additional disk space will be used.
Get:1 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic/universe amd64 libonig4 amd64 6.7.0-1 [119 kB]
Get:2 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic/universe amd64 libjq1 amd64 1.5+dfsg-2 [111 kB]
Get:3 http://us-west1.gce.archive.ubuntu.com/ubuntu bionic/universe amd64 jq amd64 1.5+dfsg-2 [45.6 kB]
Fetched 276 kB in 0s (20.9 MB/s)
Selecting previously unselected package libonig4:amd64.
(Reading database ... 100814 files and directories currently installed.)
Preparing to unpack .../libonig4_6.7.0-1_amd64.deb ...
Unpacking libonig4:amd64 (6.7.0-1) ...
Selecting previously unselected package libjq1:amd64.
Preparing to unpack .../libjq1_1.5+dfsg-2_amd64.deb ...
Unpacking libjq1:amd64 (1.5+dfsg-2) ...
Selecting previously unselected package jq.
Preparing to unpack .../jq_1.5+dfsg-2_amd64.deb ...
Unpacking jq (1.5+dfsg-2) ...
Setting up libonig4:amd64 (6.7.0-1) ...
Setting up libjq1:amd64 (1.5+dfsg-2) ...
Setting up jq (1.5+dfsg-2) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for libc-bin (2.27-3ubuntu1.4) ...
Install golang.
--2021-10-11 05:34:17--  https://dl.google.com/go/go1.13.9.linux-amd64.tar.gz
Resolving dl.google.com (dl.google.com)... 74.125.195.136, 74.125.195.91, 74.125.195.190, ...
Connecting to dl.google.com (dl.google.com)|74.125.195.136|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 120139686 (115M) [application/octet-stream]
Saving to: ‘/tmp/go1.13.9.linux-amd64.tar.gz’

go1.13.9.linux-amd64.tar.gz                      100%[=======================================================================================================>] 114.57M  40.0MB/s    in 2.9s

2021-10-11 05:34:20 (40.0 MB/s) - ‘/tmp/go1.13.9.linux-amd64.tar.gz’ saved [120139686/120139686]

Done.
Please run and add 'export PATH=$PATH:/usr/local/go/bin' into your shell profile.
You can proceed to run arktos-up.sh if you want to launch a single-node cluster.
```

and then run the following commands:
```
echo export PATH=$PATH:/usr/local/go/bin\ >> ~/.profile
echo cd \$HOME/go/src/k8s.io/arktos >> ~/.profile
source ~/.profile
```
##### Output
````bigquery
root@tesseract:~# echo export PATH=$PATH:/usr/local/go/bin\ >> ~/.profile
root@tesseract:~# echo cd \$HOME/go/src/k8s.io/arktos >> ~/.profile
root@tesseract:~# source ~/.profile
root@tesseract:~/go/src/k8s.io/arktos#
````

### Step-3: Start Arktos cluster
*Login to instance  and run following steps to deploy arktos cluster with Mizar as CNI*
```bash
cd $HOME/go/src/k8s.io/arktos
CNIPLUGIN=mizar ./hack/arktos-up.sh
```
**Finally we got  following output, which indicates that arktos cluster created successfully with Mizar as CNI**

```bigquery
root@tesseract:~/go/src/k8s.io/arktos# CNIPLUGIN=mizar  ./hack/arktos-up.sh
DBG: Flannel CNI plugin will be installed AFTER cluster is up
DBG: effective feature gates AllAlpha=false,MandatoryArktosNetwork=true,WorkloadInfoDefaulting=true,QPSDoubleGCController=true,QPSDoubleRSController=true,MandatoryArktosNetwork=true
DBG: effective disabling admission plugins
DBG: effective default network template file is /root/go/src/k8s.io/arktos/hack/testdata/default-flat-network.tmpl
DBG: kubelet arg RESOLV_CONF is /run/systemd/resolve/resolv.conf
WARNING : The kubelet is configured to not fail even if swap is enabled; production deployments should disable swap.
CNI plugin will be installed after cluster is started
Right now the minimum common cni binary package is being installed only
Ensuring minimum cni plugin installation...
installing cni plugin binaries
./
./flannel
./ptp
./host-local
./firewall
./portmap
./tuning
./vlan
./host-device
./bandwidth
./sbr
./static
./dhcp
./ipvlan
./macvlan
./loopback
./bridge
2021-10-11 05:48:32 URL:https://github-releases.githubusercontent.com/84575398/53318d00-bf61-11e9-9a8f-40364582e9ed?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20211011%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20211011T054832Z&X-Amz-Expires=300&X-Amz-Signature=11ba49b03533c211d7438ca5fec5aa2c08f162a65d999b14f92c37cbf0af74eb&X-Amz-SignedHeaders=host&actor_id=0&key_id=0&repo_id=84575398&response-content-disposition=attachment%3B%20filename%3Dcni-plugins-linux-amd64-v0.8.2.tgz&response-content-type=application%2Foctet-stream [36662740/36662740] -> "-" [1]
WARNING : The kubelet is configured to not fail even if swap is enabled; production deployments should disable swap.
Getting runtime deployment file  libvirt-qemu
--2021-10-11 05:48:32--  https://raw.githubusercontent.com/futurewei-cloud/arktos-vm-runtime/release-0.6/deploy/apparmor/libvirt-qemu
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.199.108.133, 185.199.109.133, 185.199.110.133, ...
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|185.199.108.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 6578 (6.4K) [text/plain]
Saving to: ‘/tmp/libvirt-qemu’

/tmp/libvirt-qemu                                100%[=======================================================================================================>]   6.42K  --.-KB/s    in 0s

2021-10-11 05:48:32 (74.6 MB/s) - ‘/tmp/libvirt-qemu’ saved [6578/6578]

Getting runtime deployment file  libvirtd
--2021-10-11 05:48:32--  https://raw.githubusercontent.com/futurewei-cloud/arktos-vm-runtime/release-0.6/deploy/apparmor/libvirtd
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.199.111.133, 185.199.110.133, 185.199.109.133, ...
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|185.199.111.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1617 (1.6K) [text/plain]
Saving to: ‘/tmp/libvirtd’

/tmp/libvirtd                                    100%[=======================================================================================================>]   1.58K  --.-KB/s    in 0s

2021-10-11 05:48:33 (32.8 MB/s) - ‘/tmp/libvirtd’ saved [1617/1617]

Getting runtime deployment file  virtlet
--2021-10-11 05:48:33--  https://raw.githubusercontent.com/futurewei-cloud/arktos-vm-runtime/release-0.6/deploy/apparmor/virtlet
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.199.111.133, 185.199.110.133, 185.199.109.133, ...
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|185.199.111.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2582 (2.5K) [text/plain]
Saving to: ‘/tmp/virtlet’

/tmp/virtlet                                     100%[=======================================================================================================>]   2.52K  --.-KB/s    in 0s

2021-10-11 05:48:33 (49.0 MB/s) - ‘/tmp/virtlet’ saved [2582/2582]

Getting runtime deployment file  vms
--2021-10-11 05:48:33--  https://raw.githubusercontent.com/futurewei-cloud/arktos-vm-runtime/release-0.6/deploy/apparmor/vms
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.199.111.133, 185.199.110.133, 185.199.109.133, ...
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|185.199.111.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 485 [text/plain]
Saving to: ‘/tmp/vms’

/tmp/vms                                         100%[=======================================================================================================>]     485  --.-KB/s    in 0s

2021-10-11 05:48:33 (43.3 MB/s) - ‘/tmp/vms’ saved [485/485]

Getting runtime deployment file  vmruntime.yaml
--2021-10-11 05:48:33--  https://raw.githubusercontent.com/futurewei-cloud/arktos-vm-runtime/release-0.6/deploy/data/virtlet-ds.yaml
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.199.111.133, 185.199.110.133, 185.199.109.133, ...
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|185.199.111.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 11643 (11K) [text/plain]
Saving to: ‘/tmp/vmruntime.yaml’

/tmp/vmruntime.yaml                              100%[=======================================================================================================>]  11.37K  --.-KB/s    in 0s

2021-10-11 05:48:33 (67.5 MB/s) - ‘/tmp/vmruntime.yaml’ saved [11643/11643]

Getting runtime deployment file  images.yaml
--2021-10-11 05:48:33--  https://raw.githubusercontent.com/futurewei-cloud/arktos-vm-runtime/release-0.6/deploy/images.yaml
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.199.111.133, 185.199.110.133, 185.199.109.133, ...
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|185.199.111.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 254 [text/plain]
Saving to: ‘/tmp/images.yaml’

/tmp/images.yaml                                 100%[=======================================================================================================>]     254  --.-KB/s    in 0s

2021-10-11 05:48:33 (20.2 MB/s) - ‘/tmp/images.yaml’ saved [254/254]

Stopping Apparmor service
make: Entering directory '/root/go/src/k8s.io/arktos'
make[1]: Entering directory '/root/go/src/k8s.io/arktos'
+++ [1011 05:48:38] Building go targets for linux/amd64:
    ./vendor/k8s.io/code-generator/cmd/deepcopy-gen
+++ [1011 05:48:38] Building go targets for linux/amd64:
    ./vendor/k8s.io/code-generator/cmd/defaulter-gen
+++ [1011 05:48:38] Building go targets for linux/amd64:
    ./vendor/k8s.io/code-generator/cmd/conversion-gen
+++ [1011 05:48:38] Building go targets for linux/amd64:
    ./vendor/k8s.io/kube-openapi/cmd/openapi-gen
+++ [1011 05:48:41] Building go targets for linux/amd64:
    ./vendor/github.com/go-bindata/go-bindata/go-bindata
make[1]: Leaving directory '/root/go/src/k8s.io/arktos'
Running copyright check for repo: /root/go/src/k8s.io/arktos, logging to _output/ArktosCopyrightTool.log
~/go/src/k8s.io/arktos ~/go/src/k8s.io/arktos
warning: inexact rename detection was skipped due to too many files.
warning: you may want to set your diff.renameLimit variable to at least 3062 and retry the command.
~/go/src/k8s.io/arktos
~/go/src/k8s.io/arktos ~/go/src/k8s.io/arktos
warning: inexact rename detection was skipped due to too many files.
warning: you may want to set your diff.renameLimit variable to at least 3062 and retry the command.
~/go/src/k8s.io/arktos
Inspecting copyright files, writing logs to _output/ArktosCopyrightTool.log
Done.
+++ [1011 05:48:59] Building go targets for linux/amd64:
    cmd/kubectl
    cmd/hyperkube
    cmd/kube-apiserver
    cmd/kube-controller-manager
    cmd/workload-controller-manager
    cmd/cloud-controller-manager
    cmd/kubelet
    cmd/kube-proxy
    cmd/kube-scheduler
    cmd/arktos-network-controller
Running copyright check for repo: /root/go/src/k8s.io/arktos, logging to _output/ArktosCopyrightTool.log
~/go/src/k8s.io/arktos ~/go/src/k8s.io/arktos
warning: inexact rename detection was skipped due to too many files.
warning: you may want to set your diff.renameLimit variable to at least 3062 and retry the command.
~/go/src/k8s.io/arktos
~/go/src/k8s.io/arktos ~/go/src/k8s.io/arktos
warning: inexact rename detection was skipped due to too many files.
warning: you may want to set your diff.renameLimit variable to at least 3062 and retry the command.
~/go/src/k8s.io/arktos
Inspecting copyright files, writing logs to _output/ArktosCopyrightTool.log
Done.
make: Leaving directory '/root/go/src/k8s.io/arktos'
cannot find etcd locally. will install one.
Downloading https://github.com/centaurus-cloud/etcd/releases/download/v3.4.3/etcd-v3.4.3-linux-amd64.tar.gz succeed
etcd v3.4.3 installed. To use:
export PATH="/root/go/src/k8s.io/arktos/third_party/etcd:${PATH}"

The current version is 3.4.3

API SERVER insecure port is free, proceeding...
API SERVER secure port is free, proceeding...
Unable to successfully run 'cfssl' from /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/usr/local/go/bin:/root/go/src/k8s.io/arktos/third_party/etcd; downloading instead...
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
100   623  100   623    0     0   2532      0 --:--:-- --:--:-- --:--:--  2532
100  9.8M  100  9.8M    0     0  20.3M      0 --:--:-- --:--:-- --:--:-- 20.3M
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
100   627  100   627    0     0   3300      0 --:--:-- --:--:-- --:--:--  5225
100 2224k  100 2224k    0     0  6485k      0 --:--:-- --:--:-- --:--:-- 6485k
Detected host and ready to start services.  Doing some housekeeping first...
Using GO_OUT /root/go/src/k8s.io/arktos/_output/local/bin/linux/amd64
Starting services now!
Starting etcd

The current version is 3.4.3

etcd --name tesseract --listen-peer-urls http://10.138.0.6:2380   --advertise-client-urls http://10.138.0.6:2379 --data-dir /tmp/tmp.alwRSj87Rg --listen-client-urls http://10.138.0.6:2379,http://127.0.0.1:2379 --listen-peer-urls http://10.138.0.6:2380 --debug > "/tmp/etcd.log" 2>/dev/null
Waiting for etcd to come up.
+++ [1011 05:51:49] On try 2, etcd: : {"health":"true"}
{"header":{"cluster_id":"15529568054373559649","member_id":"10928097920325379819","revision":"2","raft_term":"2"}}Starting 1 kube-apiserver instances. If you want to make changes to the kube-apiserver nubmer, please run export APISERVER_SERVER=n(n=1,2,...).
Copied the apiserver partition config file  /var/run/kubernetes/apiserver.config...
Can't load /root/.rnd into RNG
140612615614912:error:2406F079:random number generator:RAND_load_file:Cannot open file:../crypto/rand/randfile.c:88:Filename=/root/.rnd
Generating a RSA private key
.............................................+++++
...........+++++
writing new private key to '/var/run/kubernetes/server-ca.key'
-----
Can't load /root/.rnd into RNG
140268293956032:error:2406F079:random number generator:RAND_load_file:Cannot open file:../crypto/rand/randfile.c:88:Filename=/root/.rnd
Generating a RSA private key
..................+++++
........................................................+++++
writing new private key to '/var/run/kubernetes/client-ca.key'
-----
Can't load /root/.rnd into RNG
140184052535744:error:2406F079:random number generator:RAND_load_file:Cannot open file:../crypto/rand/randfile.c:88:Filename=/root/.rnd
Generating a RSA private key
..........+++++
......+++++
writing new private key to '/var/run/kubernetes/request-header-ca.key'
-----
2021/10/11 05:51:50 [INFO] generate received request
2021/10/11 05:51:50 [INFO] received CSR
2021/10/11 05:51:50 [INFO] generating key: rsa-2048
2021/10/11 05:51:50 [INFO] encoded CSR
2021/10/11 05:51:50 [INFO] signed certificate with serial number 633615672745921934471696557615031964193718214240
2021/10/11 05:51:50 [WARNING] This certificate lacks a "hosts" field. This makes it unsuitable for
websites. For more information see the Baseline Requirements for the Issuance and Management
of Publicly-Trusted Certificates, v.1.1.6, from the CA/Browser Forum (https://cabforum.org);
specifically, section 10.2.3 ("Information Requirements").
2021/10/11 05:51:50 [INFO] generate received request
2021/10/11 05:51:50 [INFO] received CSR
2021/10/11 05:51:50 [INFO] generating key: rsa-2048
2021/10/11 05:51:50 [INFO] encoded CSR
2021/10/11 05:51:50 [INFO] signed certificate with serial number 69766932639916915977289965919067680474366803193
2021/10/11 05:51:50 [WARNING] This certificate lacks a "hosts" field. This makes it unsuitable for
websites. For more information see the Baseline Requirements for the Issuance and Management
of Publicly-Trusted Certificates, v.1.1.6, from the CA/Browser Forum (https://cabforum.org);
specifically, section 10.2.3 ("Information Requirements").
2021/10/11 05:51:50 [INFO] generate received request
2021/10/11 05:51:50 [INFO] received CSR
2021/10/11 05:51:50 [INFO] generating key: rsa-2048
2021/10/11 05:51:50 [INFO] encoded CSR
2021/10/11 05:51:50 [INFO] signed certificate with serial number 452634273301324273204968214035046726283524523321
2021/10/11 05:51:50 [WARNING] This certificate lacks a "hosts" field. This makes it unsuitable for
websites. For more information see the Baseline Requirements for the Issuance and Management
of Publicly-Trusted Certificates, v.1.1.6, from the CA/Browser Forum (https://cabforum.org);
specifically, section 10.2.3 ("Information Requirements").
2021/10/11 05:51:50 [INFO] generate received request
2021/10/11 05:51:50 [INFO] received CSR
2021/10/11 05:51:50 [INFO] generating key: rsa-2048
2021/10/11 05:51:50 [INFO] encoded CSR
2021/10/11 05:51:50 [INFO] signed certificate with serial number 51533478957495997350976787813650298068964422438
2021/10/11 05:51:50 [WARNING] This certificate lacks a "hosts" field. This makes it unsuitable for
websites. For more information see the Baseline Requirements for the Issuance and Management
of Publicly-Trusted Certificates, v.1.1.6, from the CA/Browser Forum (https://cabforum.org);
specifically, section 10.2.3 ("Information Requirements").
2021/10/11 05:51:50 [INFO] generate received request
2021/10/11 05:51:50 [INFO] received CSR
2021/10/11 05:51:50 [INFO] generating key: rsa-2048
2021/10/11 05:51:51 [INFO] encoded CSR
2021/10/11 05:51:51 [INFO] signed certificate with serial number 382391674412931699791058577094748769338988129776
2021/10/11 05:51:51 [WARNING] This certificate lacks a "hosts" field. This makes it unsuitable for
websites. For more information see the Baseline Requirements for the Issuance and Management
of Publicly-Trusted Certificates, v.1.1.6, from the CA/Browser Forum (https://cabforum.org);
specifically, section 10.2.3 ("Information Requirements").
2021/10/11 05:51:51 [INFO] generate received request
2021/10/11 05:51:51 [INFO] received CSR
2021/10/11 05:51:51 [INFO] generating key: rsa-2048
2021/10/11 05:51:51 [INFO] encoded CSR
2021/10/11 05:51:51 [INFO] signed certificate with serial number 453986043716689126877943875058998644073199091360
2021/10/11 05:51:51 [WARNING] This certificate lacks a "hosts" field. This makes it unsuitable for
websites. For more information see the Baseline Requirements for the Issuance and Management
of Publicly-Trusted Certificates, v.1.1.6, from the CA/Browser Forum (https://cabforum.org);
specifically, section 10.2.3 ("Information Requirements").
2021/10/11 05:51:51 [INFO] generate received request
2021/10/11 05:51:51 [INFO] received CSR
2021/10/11 05:51:51 [INFO] generating key: rsa-2048
2021/10/11 05:51:52 [INFO] encoded CSR
2021/10/11 05:51:52 [INFO] signed certificate with serial number 147687886937495416841714459588587317172384619774
2021/10/11 05:51:52 [WARNING] This certificate lacks a "hosts" field. This makes it unsuitable for
websites. For more information see the Baseline Requirements for the Issuance and Management
of Publicly-Trusted Certificates, v.1.1.6, from the CA/Browser Forum (https://cabforum.org);
specifically, section 10.2.3 ("Information Requirements").
2021/10/11 05:51:52 [INFO] generate received request
2021/10/11 05:51:52 [INFO] received CSR
2021/10/11 05:51:52 [INFO] generating key: rsa-2048
2021/10/11 05:51:52 [INFO] encoded CSR
2021/10/11 05:51:52 [INFO] signed certificate with serial number 625097933373779609866695099435927145997367670795
2021/10/11 05:51:52 [WARNING] This certificate lacks a "hosts" field. This makes it unsuitable for
websites. For more information see the Baseline Requirements for the Issuance and Management
of Publicly-Trusted Certificates, v.1.1.6, from the CA/Browser Forum (https://cabforum.org);
specifically, section 10.2.3 ("Information Requirements").
2021/10/11 05:51:52 [INFO] generate received request
2021/10/11 05:51:52 [INFO] received CSR
2021/10/11 05:51:52 [INFO] generating key: rsa-2048
2021/10/11 05:51:52 [INFO] encoded CSR
2021/10/11 05:51:52 [INFO] signed certificate with serial number 503510828271230596022269023444739830993005630470
2021/10/11 05:51:52 [WARNING] This certificate lacks a "hosts" field. This makes it unsuitable for
websites. For more information see the Baseline Requirements for the Issuance and Management
of Publicly-Trusted Certificates, v.1.1.6, from the CA/Browser Forum (https://cabforum.org);
specifically, section 10.2.3 ("Information Requirements").
Waiting for apiserver to come up
+++ [1011 05:52:01] On try 7, apiserver: : ok
clusterrolebinding.rbac.authorization.k8s.io/kube-apiserver-kubelet-admin created
Cluster "local-up-cluster" set.
use 'kubectl --kubeconfig=/var/run/kubernetes/admin-kube-aggregator0.kubeconfig' to use the aggregated API server
2021/10/11 05:52:01 [INFO] generate received request
2021/10/11 05:52:01 [INFO] received CSR
2021/10/11 05:52:01 [INFO] generating key: rsa-2048
2021/10/11 05:52:02 [INFO] encoded CSR
2021/10/11 05:52:02 [INFO] signed certificate with serial number 621986928180665924308468173038012747518154231499
2021/10/11 05:52:02 [WARNING] This certificate lacks a "hosts" field. This makes it unsuitable for
websites. For more information see the Baseline Requirements for the Issuance and Management
of Publicly-Trusted Certificates, v.1.1.6, from the CA/Browser Forum (https://cabforum.org);
specifically, section 10.2.3 ("Information Requirements").
service/kube-dns created
serviceaccount/kube-dns created
configmap/kube-dns created
deployment.apps/kube-dns created
Kube-dns addon successfully deployed.
2021/10/11 05:52:02 [INFO] generate received request
2021/10/11 05:52:02 [INFO] received CSR
2021/10/11 05:52:02 [INFO] generating key: rsa-2048
2021/10/11 05:52:03 [INFO] encoded CSR
2021/10/11 05:52:03 [INFO] signed certificate with serial number 137769933352680725068074469567735868725516747273
2021/10/11 05:52:03 [WARNING] This certificate lacks a "hosts" field. This makes it unsuitable for
websites. For more information see the Baseline Requirements for the Issuance and Management
of Publicly-Trusted Certificates, v.1.1.6, from the CA/Browser Forum (https://cabforum.org);
specifically, section 10.2.3 ("Information Requirements").
kubelet ( 7609 ) is running.
customresourcedefinition.apiextensions.k8s.io/bouncers.mizar.com created
customresourcedefinition.apiextensions.k8s.io/dividers.mizar.com created
customresourcedefinition.apiextensions.k8s.io/droplets.mizar.com created
customresourcedefinition.apiextensions.k8s.io/endpoints.mizar.com created
customresourcedefinition.apiextensions.k8s.io/subnets.mizar.com created
customresourcedefinition.apiextensions.k8s.io/vpcs.mizar.com created
serviceaccount/mizar-operator created
clusterrolebinding.rbac.authorization.k8s.io/mizar-operator created
daemonset.apps/mizar-daemon created
deployment.apps/mizar-operator created
Create default storage class for
storageclass.storage.k8s.io/standard created
customresourcedefinition.apiextensions.k8s.io/networks.arktos.futurewei.com created
*******************************************
Setup Arktos components ...


Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
Waiting for node ready at api server
tesseract   Ready   <none>   5m33s   v0.9.0
node/tesseract labeled
configmap/virtlet-image-translations created
daemonset.apps/virtlet created
configmap/virtlet-config created
clusterrolebinding.rbac.authorization.k8s.io/virtlet created
clusterrole.rbac.authorization.k8s.io/virtlet created
clusterrole.rbac.authorization.k8s.io/configmap-reader created
clusterrole.rbac.authorization.k8s.io/virtlet-userdata-reader created
clusterrolebinding.rbac.authorization.k8s.io/kubelet-node-binding created
clusterrolebinding.rbac.authorization.k8s.io/vm-userdata-binding created
clusterrole.rbac.authorization.k8s.io/virtlet-crd created
clusterrolebinding.rbac.authorization.k8s.io/virtlet-crd created
serviceaccount/virtlet created
NAME      DESIRED   CURRENT   READY   UP-TO-DATE   AVAILABLE   NODE SELECTOR   AGE
virtlet   1         1         0       1            0           <none>          0s
clusterrole.rbac.authorization.k8s.io/system:arktos-network-reader created
clusterrolebinding.rbac.authorization.k8s.io/system:kubelet-network-reader created

Arktos Setup done.
*******************************************
Setup Kata Containers components ...
* Install Kata components
kata-containers 2.2.1 from Kata Containers (katacontainers✓) installed
* Checking Kata compatibility
time="2021-10-11T06:00:37Z" level=warning msg="Not running network checks as super user" arch=amd64 name=kata-runtime pid=2581 source=runtime time="2021-10-11T06:00:37Z" level=error msg="CPU property not found" arch=amd64 description="Virtualization support" name=vmx pid=2581 source=runtime type=flag time="2021-10-11T06:00:38Z" level=warning msg="modprobe insert module failed" arch=amd64 error="exit status 1" module=kvm_intel name=kata-runtime output="modprobe: ERROR: could not insert 'kvm_intel': Operation not supported\n" pid=2581 source=runtime time="2021-10-11T06:00:38Z" level=error msg="kernel property not found" arch=amd64 description="Intel KVM" name=kvm_intel pid=2581 source=runtime type=module time="2021-10-11T06:00:38Z" level=error msg="ERROR: System is not capable of running Kata Containers" arch=amd64 name=kata-runtime pid=2581 source=runtime ERROR: System is not capable of running Kata Containers
Aborted. Current system does not support Kata Containers.
Kata Setup done.
*******************************************
Local Kubernetes cluster is running. Press Ctrl-C to shut it down.

Logs:
  /tmp/kube-apiserver0.log
  /tmp/kube-controller-manager.log


  /tmp/kube-proxy.log
  /tmp/kube-scheduler.log
  /tmp/kubelet.log

To start using your cluster, you can open up another terminal/tab and run:

  export KUBECONFIG=/var/run/kubernetes/admin.kubeconfig
Or
  export KUBECONFIG=/var/run/kubernetes/adminN(N=0,1,...).kubeconfig

  cluster/kubectl.sh

Alternatively, you can write to the default kubeconfig:

  export KUBERNETES_PROVIDER=local

  cluster/kubectl.sh config set-cluster local --server=https://tesseract:6443 --certificate-authority=/var/run/kubernetes/server-ca.crt
  cluster/kubectl.sh config set-credentials myself --client-key=/var/run/kubernetes/client-admin.key --client-certificate=/var/run/kubernetes/client-admin.crt
  cluster/kubectl.sh config set-context local --cluster=local --user=myself
  cluster/kubectl.sh config use-context local
  cluster/kubectl.sh
```

##### *Leave this terminal here as it is (do not close the terminal) and open new terminal of same instance*

### Step-4 Check Cluster health
Open new terminal for same instance and run following commands:

##### Check node status
```bigquery
./cluster/kubectl.sh  get node
```
***Output***
```bigquery
root@tesseract:~/go/src/k8s.io/arktos# kubectl get node -o wide
NAME        STATUS   ROLES    AGE   VERSION   INTERNAL-IP   EXTERNAL-IP   OS-IMAGE             KERNEL-VERSION   CONTAINER-RUNTIME
tesseract   Ready    <none>   4m   v0.9.0    10.138.0.6    <none>        Ubuntu 18.04.6 LTS   5.6.0-rc2        containerd://1.4.0-beta.1-29-g70b0d3cf
root@tesseract:~/go/src/k8s.io/arktos#
```

##### Check pods status
```bigquery
./cluster/kubectl.sh get pods -Ao wide
```
***Output***
```bigquery
root@tesseract:~# ./cluster/kubectl.sh get pods  -Ao wide
NAMESPACE     NAME                               HASHKEY               READY   STATUS        RESTARTS   AGE   IP               NODE      NOMINATED NODE   READINESS GATES
default       mizar-daemon-svg8z                 5915807583702037959   1/1     Running       0          21m   10.138.0.6     tesseract   <none>           <none>
default       mizar-operator-6f5ddb6fd5-g5s4p    5690885477719514628   1/1     Running       0          21m   10.138.0.6     tesseract   <none>           <none>
kube-system   coredns-default-647bcd544d-rtrrg   1232052352497091929   1/1     Running       0          21m   20.0.0.26      tesseract   <none>           <none>
kube-system   kube-dns-7f4bf79dc-5w97x           869072982459874969    3/3     Running       0          17m   20.0.0.30      tesseract   <none>           <none>
kube-system   virtlet-mzvhl                      8706931631410429083   3/3     Running       1          20m   10.138.0.6     tesseract   <none>           <none>
```

##### Check vpcs
```bigquery
./cluster/kubectl.sh get vpc -Ao wide
```
***Output***

root@tesseract:~# ./cluster/kubectl.sh get vpcs  -o wide
NAME   IP         PREFIX   VNI   DIVIDERS   STATUS        CREATETIME                   PROVISIONDELAY
vpc0   20.0.0.0   8        1     1          Provisioned   2021-10-11T09:32:39.275336   21.090225
root@tesseract:~#


##### Check subnets
```bigquery
./cluster/kubectl.sh get subnet -Ao wide
```
***Output***
```bigquery
root@tesseract:~# ./cluster/kubectl.sh get dividers  -Ao wide
NAMESPACE   NAME                                          VPC    IP              MAC                 DROPLET            STATUS        CREATETIME                 PROVISIONDELAY
default     vpc0-d-e18dc3da-9247-4b97-a398-00c7b98e80ce   vpc0   10.138.0.6   00:50:56:af:9c:23      tesseract          Provisioned   2021-10-11T09:33:00.353292   0.268504
root@tesseract:~#
```

##### Check dividers
```bigquery
./cluster/kubectl.sh get dividers -Ao wide
```
***Output***
```bigquery
root@tesseract:~# ./cluster/kubectl.sh get dividers  -Ao wide
NAMESPACE   NAME                                          VPC    IP              MAC                 DROPLET            STATUS        CREATETIME                  PROVISIONDELAY
default     vpc0-d-e18dc3da-9247-4b97-a398-00c7b98e80ce   vpc0   10.138.0.6   00:50:56:af:9c:23      tesseract          Provisioned   2021-10-11T09:33:00.353292   0.268504
root@tesseract:~#
```

##### Check bouncers
```bigquery
./cluster/kubectl.sh get bouncers -Ao wide
```
***Output***
```bigquery
root@tesseract:~# ./cluster/kubectl.sh get bouncers  -Ao wide
NAMESPACE   NAME                                          VPC    NET    IP              MAC                 DROPLET            STATUS        CREATETIME           PROVISIONDELAY
default     net0-b-6dac6de3-1109-4ce3-8d70-1322bd674a3b   vpc0   net0   10.138.0.6   00:50:56:af:9c:23      tesseract        Provisioned   2021-10-11T09:33:01.085738   1.871973
root@tesseract:~#
```

##### Check networks
```bigquery
./cluster/kubectl.sh get net
```
***Output***
```bigquery
root@tesseract:~# ./cluster/kubectl.sh get net  -Ao wide
NAME      TYPE    VPC                      PHASE   DNS
default   mizar   system-default-network   Ready   10.0.0.86
root@tesseract:~#
```

##### check pods status after deploying application pods (kafka and zookeeper pods)
```bigquery
./cluster/kubectl.sh get pods -Ao wide
```
***Output***
```bigquery
root@tesseract:~# ./cluster/kubectl.sh get pods  -Ao wide 
NAMESPACE     NAME                               HASHKEY               READY   STATUS            RESTARTS    AGE    IP              ODE      NOMINATED NODE   READINESS GATES
default       kafka-556d74b878-tlcnb             8334294799958598409   1/1     CrashLoopBackOff   2          2m   20.0.0.18      tesseract   <none>           <none>
default       mizar-daemon-svg8z                 5915807583702037959   1/1     Running            0          21m   10.138.0.6     tesseract   <none>           <none>
default       mizar-operator-6f5ddb6fd5-g5s4p    5690885477719514628   1/1     Running            0          21m   10.138.0.6     tesseract   <none>           <none>
default       zookeeper-6d5ff49b84-qlgx9         5218200621973899165   1/1     Running            0          2m   20.0.0.49      tesseract   <none>           <none>
kube-system   coredns-default-647bcd544d-rtrrg   1232052352497091929   1/1     Running            0          21m   20.0.0.26      tesseract   <none>           <none>
kube-system   kube-dns-7f4bf79dc-5w97x           869072982459874969    3/3     Running            0          17m   20.0.0.30      tesseract   <none>           <none>
kube-system   virtlet-mzvhl                      8706931631410429083   3/3     Running            1          20m   10.138.0.6     tesseract   <none>           <none>
```

##### Check services
```bigquery
./cluster/kubectl.sh get svc
```
***Output***
```bigquery
root@tesseract:~# ./cluster/kubectl.sh get svc
NAME                 TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)    AGE
kafka                ClusterIP   10.0.0.104   <none>        9092/TCP   2m
kubernetes           ClusterIP   10.0.0.1     <none>        443/TCP    21m
kubernetes-default   ClusterIP   10.0.0.196   <none>        443/TCP    21m
zookeeper            ClusterIP   10.0.0.146   <none>        2181/TCP   2m
root@tesseract:~# 
```

Events of kafka:
  
```bigquery
Events:
  Type     Reason     Age                From               Message
  ----     ------     ----               ----               -------
  Normal   Scheduled  55s                default-scheduler  Successfully assigned default/kafka-7b88788f47-6dntk to node1
  Normal   Logging    54s                kopf               Creation event is processed: 1 succeeded; 0 failed.
  Normal   Logging    54s                kopf               Handler 'builtins_on_pod' succeeded.
  Normal   Pulled     15s (x3 over 51s)  kubelet            Container image "wurstmeister/kafka:2.11-2.0.1" already present on machine
  Normal   Created    15s (x3 over 51s)  kubelet            Created container kafka
  Normal   Started    14s (x3 over 51s)  kubelet            Started container kafka
  Warning  BackOff    5s (x2 over 28s)   kubelet            Back-off restarting failed container
  ```
