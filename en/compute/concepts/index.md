---
title: Resource relationships in {{ compute-full-name }}
description: This tutorial describes relationships between {{ compute-short-name }} resources, resource types, and relationships with other {{ yandex-cloud }} services.
---

# Resource relationships in {{ compute-full-name }}

All resources in {{ compute-short-name }} break down into three types:

* _Basic_ resources, which include [virtual machines](vm.md) and [disks](disk.md).
* _Auxiliary_ resources, which include [snapshots](snapshot.md) and [images](image.md). These resources are only used for creating other resources.
* _Information_ resources, such as disk types and availability zones. These resources are read-only.

In addition, when creating VMs, {{ compute-short-name }} uses resources of other services, such as subnets and folders.

## Basic resources {#basic-resource}

{{ compute-short-name }} allows you to create VMs and attach disks to them.

A VM must have at least one disk attached, which is a boot disk. You can create a new empty disk or restore one from a snapshot or image.

## Auxiliary resources {#auxillary-resource}

Snapshots and images are mainly designed for saving and restoring data disks.

You can only create a snapshot from a disk. Snapshot information contains the ID of its source disk.

As for an image, you can create it from a disk, snapshot, another image, or file.

## Information resources {#information-resource}

When creating disks and VMs, you need to specify the [availability zone](../../overview/concepts/geo-scope.md) where they will reside; disk images and snapshots are not associated with any availability zones.

You can view a list of availability zones and find out their current status.

When creating a disk, you also specify the disk type. You can view possible disk types and find out in which zones they are available.

## Relationship with resources of other services {#relationship-with-resources-of-other-services}

When creating a VM, you need to specify the subnet it will be connected to. You can find more information about cloud networks [here](../../vpc/concepts/network.md).

All {{ compute-short-name }} resources are created within folders. Disk types and availability zones are public resources that do not belong to any folder. You can learn more about the resource hierarchy in {{ yandex-cloud }} [here](../../resource-manager/concepts/resources-hierarchy.md).
