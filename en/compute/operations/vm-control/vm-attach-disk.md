# Attaching a disk to a VM

You can attach an extra [disk](../../concepts/disk.md) to [either a running or stopped VM](../../concepts/vm-statuses.md).

{% include [second-disk-without-restart](../../../_includes/compute/second-disk-without-restart.md) %}

{% include [disk-auto-delete](../../_includes_service/disk-auto-delete.md) %}

## Attaching a disk {#attach}


{% note info %}

You can only attach a local disk to a VM on a [dedicated host](../../concepts/dedicated-host.md) while creating it. For more information, see [this guide](../index.md#dedicated-host).

{% endnote %}


{% list tabs group=instructions %}

- Management console {#console}

   1. In the [management console]({{ link-console-main }}), select the [folder](../../../resource-manager/concepts/resources-hierarchy.md#folder) the VM belongs to.
   1. Select **{{ ui-key.yacloud.iam.folder.dashboard.label_compute }}**.
   1. In the left-hand panel, select ![image](../../../_assets/console-icons/hard-drive.svg) **{{ ui-key.yacloud.compute.switch_disks }}**.
   1. Select an unattached disk or [create](../disk-create/empty.md) a new one.
   1. Next to the disk you want to attach, click ![image](../../../_assets/console-icons/ellipsis.svg) and select **{{ ui-key.yacloud.compute.disks.button_action-attach }}**.
   1. In the window that opens:
      * In the **{{ ui-key.yacloud.compute.attach-disk.field_instance }}** field, select the virtual machine you want to mount your disk to.


      * To attach an [encrypted](../../concepts/encryption.md) disk, select a [service account](../../../iam/concepts/users/service-accounts.md) with the `kms.keys.encrypterDecrypter` [role](../../../kms/security/index.md#kms-keys-encrypterDecrypter) for the [{{ kms-short-name }} key](../../../kms/concepts/key.md) that was used to encrypt the disk.


      * Enter a device name.
      * Enable the **{{ ui-key.yacloud.compute.field_disk-autodelete }}** option if needed.
   1. Click **{{ ui-key.yacloud.compute.attach-disk.button_attach }}**.

- CLI {#cli}

   {% include [cli-install](../../../_includes/cli-install.md) %}

   {% include [default-catalogue](../../../_includes/default-catalogue.md) %}

   1. View a description of the CLI attach disk command:

      ```bash
      yc compute instance attach-disk --help
      ```

   1. Get a list of VMs in the default [folder](../../../resource-manager/concepts/resources-hierarchy.md#folder):

      {% include [compute-instance-list](../../_includes_service/compute-instance-list.md) %}

   1. Select the `ID` or `NAME` of the VM, e.g., `first-instance`.
   1. Get a list of disks in the default folder:

      {% include [compute-disk-list](../../../_includes/compute/disk-list.md) %}

   1. Select the `ID` or `NAME` of the required disk, e.g., `first-disk`. To view a list of disks attached to the VM, run the command:

      ```bash
      yc compute instance get --full first-instance
      ```

   1. Attach the disk to the VM:

      ```bash
      yc compute instance attach-disk first-instance \
        --disk-name first-disk \
        --mode rw
      ```

      To automatically delete the disk when deleting the VM, set the `--auto-delete` flag.

      {% include [attach_empty_disk](../../_includes_service/attach-empty-disk.md) %}

      If an error occurs, stop the VM:

      ```bash
      yc compute instance stop first-instance
      ```

      Then reattach the disk.
   1. If the VM was stopped, restart it:

      ```bash
      yc compute instance start first-instance
      ```

- API {#api}

   Use the [attachDisk](../../api-ref/Instance/attachDisk.md) REST API method for the [Instance](../../api-ref/Instance/) resource or the [InstanceService/AttachDisk](../../api-ref/grpc/Instance/attachDisk.md) gRPC API call.

{% endlist %}

## Mounting a disk created from a snapshot or image {#mount-disk-and-fix-uuid}

{% list tabs group=operating_system %}

- Linux {#linux}

   1. [Attach](#attach) a disk to a VM instance.
   1. [Connect](../vm-connect/ssh.md) to the VM over SSH.
   1. Run the `blkid` command and make sure that there are no partitions with duplicate UUIDs:

      ```bash
      sudo blkid
      ```

      Result:

      ```text
      /dev/vda2: UUID="0d6dfef0-542d-47ba-b55b-18ab5f5f9210" TYPE="ext4" PARTUUID="752aa845-94ee-4850-9188-71c2f919ee7b"
      /dev/vdb2: UUID="0d6dfef0-542d-47ba-b55b-18ab5f5f9210" TYPE="ext4" PARTUUID="752aa845-94ee-4850-9188-71c2f919ee7b"
      ...
      ```

   1. If there are, generate a new UUID for the duplicates that come last in the `blkid` command output. In the example from the previous step, you need to generate a UUID for the `/dev/vdb2` partition:

      ```bash
      sudo e2fsck -f /dev/vdb2
      sudo tune2fs -U $(uuidgen) /dev/vdb2
      ```

      This method works for partitions with `ext2`, `ext3`, and `ext4 `file systems. The latter is used in the Linux images provided by {{ yandex-cloud }}. The file system type is returned by the `blkid` command in the `TYPE` parameter.

      If you have a different file system, use the appropriate commands. For example, for `XFS`, execute:

      ```bash
      sudo xfs_admin -U generate /dev/vdb2
      ```

      To see if the UUID changed, run the `blkid` command again:

      ```bash
      sudo blkid
      ```

      Result:

      ```text
      /dev/vda2: UUID="0d6dfef0-542d-47ba-b55b-18ab5f5f9210" TYPE="ext4" PARTUUID="752aa845-94ee-4850-9188-71c2f919ee7b"
      /dev/vdb2: UUID="ea004485-07fb-4128-b20d-e408db1e8ae8" TYPE="ext4" PARTUUID="752aa845-94ee-4850-9188-71c2f919ee7b"
      ...
      ```

      {% include [include](../../../_includes/compute/duplicated-uuid-note.md) %}

   1. {% include [include](../../../_includes/compute/mount-disk.md) %}

   1. Run the `df` command to check the state of the file system.

- Windows {#windows}

   1. Connect to the VM [via RDP](../vm-connect/rdp.md).
   1. Run **Computer Management** (the `compmgmt.msc` snap-in) as an administrator.
   1. Under **Storage**, select **Disk Management**.

      {% note info %}

      When you attach a disk to a running VM, it might not appear in the list. In that case, restart the OS and repeat steps 1 and 2 of this guide.

      {% endnote %}

   1. If the attached disk is **Offline**, right-click it and select **Online**.
   1. Assign a letter to the attached disk if needed. For information about how to do this, see the [Microsoft documentation]({{ ms.docs }}/windows-server/storage/disk-management/change-a-drive-letter).
   1. Open **Explorer** to check that the attached disk is properly mounted and available.

{% endlist %}

## Partitioning and mounting an empty disk {#mount}

{% list tabs group=operating_system %}

- Linux {#linux}

   1. [Attach](#attach) an empty disk to the VM.
   1. [Connect to the VM via SSH](../vm-connect/ssh.md).
   1. Check whether the disk is attached as a device and get its path in the system:

      ```bash
      ls -la /dev/disk/by-id
      ```

      Result:

      ```text
      total 0
      drwxr-xr-x 2 root root 140 Jan 16 12:09 .
      drwxr-xr-x 6 root root 120 Jan 13 13:51 ..
      lrwxrwxrwx 1 root root   9 Jan 16 12:09 virtio-fhm1dn62tm5d******** -> ../../vdc
      lrwxrwxrwx 1 root root   9 Jan 13 13:51 virtio-fhm4ev6dodt9******** -> ../../vdb
      lrwxrwxrwx 1 root root  10 Jan 13 13:51 virtio-fhm4ev6dodt9********-part1 -> ../../vdb1
      lrwxrwxrwx 1 root root  10 Jan 13 13:51 virtio-fhm4ev6dodt9********-part2 -> ../../vdb2
      lrwxrwxrwx 1 root root   9 Jan 13 13:51 virtio-nvme-disk-0 -> ../../vda
      ```

      Where:
      * Network disk links have the `virtio-<disk_ID>` format. For example, `virtio-fhm1dn62tm5d******** -> ../../vdc` means that an unpartitioned disk with the `fhm1dn62tm5d********` ID is labeled `vdc`.
      * Local disks on [dedicated hosts](../../concepts/dedicated-host.md) have links, such as `virtio-nvme-disk-<disk_number>` (if you attached the disks to your VM when creating it). Disk numbering starts from zero. For example, `virtio-nvme-disk-0 -> ../../vda` means that the first local disk (numbered zero) is labeled `vda`.

   1. Partition your disk. To do this, create [partitions](https://help.ubuntu.com/stable/ubuntu-help/disk-partitions.html.en) using the `cfdisk` [utility](https://manpages.ubuntu.com/manpages/xenial/en/man8/cfdisk.8.html), the `fdisk` [utility](https://manpages.ubuntu.com/manpages/xenial/en/man8/fdisk.8.html), or the `parted` [utility](https://manpages.ubuntu.com/manpages/xenial/en/man8/parted.8.html).

      Run commands as a superuser. To do this, use `sudo` in each command, or run the `sudo su -` command initially to switch to the superuser in the terminal. For example, let's create partitions using `fdisk`:

      1. Run the utility:

         ```bash
         sudo fdisk /dev/<disk_label>
         ```

         Where `<disk_label>` is the label of the disk to be partitioned, e.g., `vdb` or `vdc`.

         You will be taken to the `fdisk` menu. To get a list of available commands, type `m` and press **Enter**.
      1. Create a new partition: type `n` and press **Enter**.
      1. Specify that the partition will be primary: type `p` and press **Enter**.
      1. You will be prompted to select a partition number. Press **Enter** to create partition `1`.
      1. Leave the default values for the numbers of the first and last sectors of the partition: press **Enter** twice.
      1. Make sure the partition has been created. To do this, request a list of disk partitions: type `p` and press **Enter**.

         Result:

         ```text
         Device     Boot Start      End  Sectors Size Id Type
         /dev/vdc1        2048 41943039 41940992  20G 83 Linux
         ```

         Where `vdc1` is the _partition label_ consisting of a disk label and a partition number. You will need the partition label for further actions with the partition.

      1. To save your changes, type `w` and press **Enter**.

   1. Format the partition to the required file system. To do this, you can use the `mkfs` [utility](https://manpages.ubuntu.com/manpages/xenial/en/man8/mkfs.8.html). For example, to format a partition to `ext4`, run the command, specifying the label of the previously created partition:

      ```bash
      sudo mkfs.ext4 /dev/<partition_label>
      ```

      Result:

      ```text
      Creating filesystem with 261888 4k blocks and 65536 inodes
      Filesystem UUID: 584a800c-e1fc-4f66-9228-a444f2d7440d
      Superblock backups stored on blocks:
              32768, 98304, 163840, 229376

      Allocating group tables: done
      Writing inode tables: done
      Creating journal (4096 blocks): done
      Writing superblocks and filesystem accounting information: done
      ```

      Where `Filesystem UUID` is the unique _partition ID_. You will need the partition ID when setting up automatic mounting of this partition to the system. You can also get the partition ID using the `sudo blkid /dev/<partition_label>` command.

   1. Mount the disk partition using the `mount` [utility](https://manpages.ubuntu.com/manpages/xenial/en/man8/mount.8.html). To mount a partition named `/dev/<partition_label>` to the `/mnt/new_disk` directory, run the following command:

      ```bash
      sudo mkdir /mnt/new_disk && sudo mount /dev/<partition_label> /mnt/new_disk
      ```

   1. Configure the partition write and read permissions using the `chmod` [utility](https://manpages.ubuntu.com/manpages/jammy/en/man1/chmod.1.html). For example, to allow all users to write to the partition, run the following command:

      ```bash
      sudo chmod a+w /mnt/new_disk
      ```

   1. Configure automatic mounting of the partition to the `mnt/new_disk` directory when the VM starts:

      1. Open the `/etc/fstab` file using the `nano` text editor:

         ```bash
         sudo nano /etc/fstab
         ```

      1. Add the following line to the end of the file, specifying the ID of your partition in the `UUID` parameter:

         ```text
         UUID=<partition_ID> /mnt/new_disk ext4 defaults 0 2
         ```

         Where `UUID` is the unique partition ID obtained earlier during formatting, e.g., `584a800c-e1fc-4f66-9228-a444f2d7440d`.

      1. Save the changes and close the file.

   1. Check the state of your file systems:

      ```bash
      df
      ```

      Result:

      ```text
      Filesystem     1K-blocks    Used Available Use% Mounted on
      udev              989424       0    989424   0% /dev
      tmpfs             203524     816    202708   1% /run
      /dev/vdb2       13354932 2754792  10015688  22% /
      tmpfs            1017608       0   1017608   0% /dev/shm
      tmpfs               5120       0      5120   0% /run/lock
      tmpfs            1017608       0   1017608   0% /sys/fs/cgroup
      tmpfs             203520       0    203520   0% /run/user/1000
      /dev/vdc1         523260    3080    520180   1% /mnt/vdc1
      ```

- Windows {#windows}

   1. Connect to the VM [via RDP](../vm-connect/rdp.md).
   1. Run **Computer Management** (the `compmgmt.msc` snap-in) as an administrator.
   1. Under **Storage**, select **Disk Management**.

      {% note info %}

      When you attach a disk to a running VM, it might not appear in the list. In that case, restart the OS and repeat steps 1 and 2 of this guide.

      {% endnote %}

   1. If the attached disk is **Offline**, right-click it and select **Online**.
   1. Initialize the disk. To do this, right-click it and select **Initialize Disk**. This opens the **Initialize Disk** dialog.
   1. Select a [partition style]({{ ms.docs }}/windows-server/storage/disk-management/initialize-new-disks#about-partition-styles---gpt-and-mbr) and click **OK**.
   1. Create partitions on the disk. To do this, right-click the empty disk and select **New Simple Volume**.
   1. Use the **New Simple Volume Wizard** to set the required partition size, [assign a drive letter]({{ ms.docs }}/windows-server/storage/disk-management/change-a-drive-letter), and specify the file system type.
   1. Open **Explorer** to check that the attached disk is properly mounted and available.

{% endlist %}