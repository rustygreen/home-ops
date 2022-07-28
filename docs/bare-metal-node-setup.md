# Bare Metal Node Setup

The following steps are necessary to setup prior to joining a new node to the cluster (or prior to bootstrapping the cluster).

## Physical Node Setup

1. Install [Fedora 36 Server](https://getfedora.org/en/server/download/)
2. Install extra disk for storage purposes
3. Determine the new disk device `sudo lsblk --fs`
3. Partition storage device (if needed)

```bash
sudo parted /dev/sdb mklabel gpt
sudo parted -a opt /dev/sdb mkpart primary ext4 0% 100%
```

## Create Storage Directory

1. Create storage directory to mount to

```bash
sudo mkdir -p /mnt/storage
```

2. Set permissions on folder

```bash
sudo chmod -R 744 /mnt/storage
```

## Mount Storage

1. Get device UUID (copy appropriate device's UUID to clipboard)
2. Copy UUID for appropriate device

```bash
sudo lsblk --fs
```

3. Edit `fstab` file

```bash
sudo nano /etc/fstab
```

4. Create new record

```bash
# ... previous entries
UUID=<YOUR_COPIED_UUID> /mnt/storage ext4 defaults 0 2
```

5. Check your work

```bash
sudo findmnt --verify
```

6. Restart machine

```bash
sudo reboot
```

7. Confirm mount

```bash
sudo lsblk --fs
```

## Install 