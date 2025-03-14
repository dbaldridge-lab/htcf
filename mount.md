# Mounting remote filesystems locally (MacOS) - *Testing failed, need permissions for ceph.client.admin.keyring. Ask to setuid bit?*
Access a wider variety of filesystems locally by using a FUSE client. This includes CephFS (e.g. /LTS, /ref) and S3 (e.g. LTOS).

## Download macFUSE
Go to [https://osxfuse.github.io/](https://osxfuse.github.io/).

Download and install the latest release:

![image](https://github.com/user-attachments/assets/efd101d7-d01a-4b12-9f92-3266bb10dd11)
![image](https://github.com/user-attachments/assets/fc3c8698-1beb-4c7a-9a57-7ec5f1c36253)

Enable System Extensions as needed:

![image](https://github.com/user-attachments/assets/274c905e-c993-488d-b254-bcdadcf39551)

![image](https://github.com/user-attachments/assets/002e1413-6927-4a5f-8c72-73e52a0ed080)

## Create a mount point
Create a directory where you want to mount the filesystem locally.
```
mkdir -p /path/to/mount/point # e.g. ~/lts
```

# Copy files from the remote host to your local machine
```
scp username@mon_host:/etc/ceph/ceph.client.admin.keyring /path/to/mount/point/ceph.client.admin.keyring
scp username@mon_host:/etc/ceph/ceph.conf /path/to/mount/point/ceph.conf
```

# Set the environment variable
export CEPH_CONF=/path/to/mount/point/ceph.conf

# Run the ceph command
ceph --keyring /path/to/mount/point/ceph.client.admin.keyring mon dump


## Mount using ceph-fuse
Use the ceph-fuse command to mount the CephFS:
```
ceph-fuse -m <mon_host>:/ /path/to/mount/point
```
Replace <mon_host> with the address of your Ceph monitor host and /path/to/mount/point with the directory you created.

## Verify
Check that the filesystem is mounted:
```
df -h /path/to/mount/point
```

