

Test app for Binder, wrote by C++ language.


compile:
a. �ļ�����frameworks/testing/APP_0004_Binder_CPP_App
b. cd /work/android-5.0.2/
   . setenv
   lunch //ѡ��23. full_tiny4412-eng
c. cd frameworks/testing/APP_0004_Binder_CPP_App
   mmm .   

test:
a. rebuid zImage to support NFS
make menuconfig
<*>   NFS client support                                                        | |
[*]     NFS client support for NFS version 3                                    | |
[*]       NFS client support for the NFSv3 ACL protocol extension               | |
[*]     NFS client support for NFS version 4                                    | |
[*]       NFS client support for NFSv4.1 (EXPERIMENTAL) 

make zImage, use zImage to boot the board

b. mount nfs
   su
   ifconfig eth0 192.168.1.100
   busybox mount -t nfs -o nolock,vers=2 192.168.1.123:/work/nfs_root /mnt
   

c. run test_server, test_client

   ./test_server &
   logcat HelloService:* *:S &
   ./test_client hello
   ./test_client hello weidongshan
