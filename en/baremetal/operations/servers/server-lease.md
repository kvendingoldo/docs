---
title: How to lease a server in {{ baremetal-full-name }}
description: Follow this guide to lease a server in {{ baremetal-full-name }}.
---

# Leasing a server

{% list tabs group=instructions %}

- Management console {#console}

  1. In the [management console]({{ link-console-main }}), select the folder you want to lease a server in.
  1. In the list of services, select **{{ baremetal-name }}**.
  1. Click **Order server**.
  1. Select the [availability zone](../../../overview/concepts/geo-scope.md) the server will be leased in.
  1. Select the [pool](../../concepts/index.md#server-pools) the server will be leased from.
  1. Under **{{ ui-key.yacloud.baremetal.title_section-server-config }}**:
  
     1. Select the [server configuration](../../concepts/server-configurations.md).
     1. Configure disk partitioning:

        1. Click **{{ ui-key.yacloud.baremetal.action_disk-layout-settings }}**.
        1. Specify the partitioning parameters. To create a new partition, click ![icon](../../../_assets/console-icons/plus.svg) **{{ ui-key.yacloud.baremetal.actions_add-partition }}**.

           {% note info %}

           To build RAID arrays and configure disk partitions yourself, click **{{ ui-key.yacloud.baremetal.action_destroy-raid }}**.

           {% endnote %}

        1. Click **{{ ui-key.yacloud.common.save }}**.
  
  1. Under **{{ ui-key.yacloud.baremetal.title_section-server-product }}**, select one of the available OS images. You can [upload your own image](../image-upload.md) and use it.
  1. Under **{{ ui-key.yacloud.baremetal.title_section-lease-conditions }}**:

     1. Specify the number of servers you want to lease.
     1. Select the period you want to lease the servers for.
  
  1. Under **{{ ui-key.yacloud.baremetal.title_section-server-network-settings }}**:

     1. Specify the ID of an existing [private subnet](../../concepts/index.md#private-subnet) or click **{{ ui-key.yacloud.common.create }}** to create a new one.

        If you do not have a subnet, click ![image](../../../_assets/console-icons/plus.svg) **{{ ui-key.yacloud.baremetal.action-create-subnetwork }}** and create one:

        * In the window that opens, enter a name and description for your subnet.
        * Click **Create subnet**.

     1. In the **{{ ui-key.yacloud.baremetal.field_needed-public-ip }}** field, choose a method for public IP address assignment:

        * `{{ ui-key.yacloud.baremetal.label_public-ip-auto }}`: To assign a random IP address.
        * `{{ ui-key.yacloud.baremetal.label_public-ip-no }}`: Not to assign a public IP address.
  
  1. Under **{{ ui-key.yacloud.baremetal.title_server-access }}**:

     1. Enter the username into the **{{ ui-key.yacloud.baremetal.field_server-user }}** field.
     1. In the **{{ ui-key.yacloud.baremetal.field_password }}** field, enter or generate a user password.
     1. In the **{{ ui-key.yacloud.baremetal.field_ssh-public-key }}** field, paste the contents of the public key file. You need to [create](../../../compute/operations/vm-connect/ssh.md#creating-ssh-keys) an SSH key pair yourself.

  1. Under **{{ ui-key.yacloud.baremetal.title_section-server-info }}**:

     1. Enter the server name in the **{{ ui-key.yacloud.baremetal.field_name }}** field.
     1. (Optional) Add **{{ ui-key.yacloud.baremetal.field_description }}** to the server.
     1. (Optional) Set **{{ ui-key.yacloud.component.label-set.label_labels }}**.
  
  1. Click **Order server**.

{% endlist %}
