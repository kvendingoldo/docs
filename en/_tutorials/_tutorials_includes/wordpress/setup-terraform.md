1. [Prepare your cloud](#before-begin).
1. [Create an infrastructure](#deploy).
1. [Configure WordPress](#wordpress-config).

If you no longer need the resources you created, [delete them](#clear-out).

## Prepare your cloud {#before-you-begin}

{% include [before-you-begin](../../_tutorials_includes/before-you-begin.md) %}

{% include [network-is-exist](../../_tutorials_includes/network-is-exist.md) %}

### Required paid resources {#paid-resources}

{% include [paid-resources-wp](../../_tutorials_includes/wordpress/paid-resources-wp.md) %}

## Create an infrastructure {#deploy}

{% include [terraform-definition](../../_tutorials_includes/terraform-definition.md) %}

To create an infrastructure using {{ TF }}:
1. [Install {{ TF }}](../../../tutorials/infrastructure-management/terraform-quickstart.md#install-terraform), [get the authentication credentials](../../../tutorials/infrastructure-management/terraform-quickstart.md#get-credentials), and specify the source for installing the {{ yandex-cloud }} provider (see [{#T}](../../../tutorials/infrastructure-management/terraform-quickstart.md#configure-provider), step 1).
1. Prepare files with the infrastructure description.

   {% list tabs group=infrastructure_description %}

   - Ready-made archive {#ready}

      1. Create a directory for files.
      1. Download the [archive](https://{{ s3-storage-host }}/www.example.com/doc-files/wordpress.zip) (1 KB).
      1. Unpack the archive to the directory. The `wordpress.tf` file should be added to the directory.

   - Manually {#manual}

      1. Create a directory for files.
      1. Create the `wordpress.tf` configuration file in the directory:

         {% cut "wordpress.tf" %}

         {% include [wordpress-tf-config](../../../_includes/web/wordpress-tf-config.md) %}

         {% endcut %}

   {% endlist %}

   For more information about the parameters of resources used in {{ TF }}, see the provider documentation:
   * [VM instance](../../../compute/concepts/vm.md): [yandex_compute_instance]({{ tf-provider-resources-link }}/compute_instance)
   * [Security groups](../../../vpc/concepts/security-groups.md): [yandex_vpc_security_group]({{ tf-provider-resources-link }}/yandex_vpc_security_group)
   * [Network](../../../vpc/concepts/network.md#network): [yandex_vpc_network]({{ tf-provider-resources-link }}/vpc_network)
   * [Subnets](../../../vpc/concepts/network.md#subnet): [yandex_vpc_subnet]({{ tf-provider-resources-link }}/vpc_subnet)
   * [DNS zone](../../../dns/concepts/dns-zone.md): [yandex_dns_zone]({{ tf-provider-resources-link }}/dns_zone)
   * [DNS resource record](../../../dns/concepts/resource-record.md): [yandex_dns_recordset]({{ tf-provider-resources-link }}/dns_recordset)
1. Under `metadata`, enter the metadata for creating a VM instance: `<username>:<SSH_key_contents>`. Regardless of the username specified, the key is assigned to the user set in the WordPress image configuration. Such users vary depending on an image. For more information, see [{#T}](../../../compute/concepts/vm-metadata.md#keys-processed-in-public-images).
1. Create resources:

   {% include [terraform-validate-plan-apply](../../_tutorials_includes/terraform-validate-plan-apply.md) %}

## Configure WordPress {#wordpress-config}

To configure WordPress:

{% list tabs group=instructions %}

- Management console {#console}

   {% include [wordpress-config](wordpress-config.md) %}

{% endlist %}

## How to delete the resources you created {#clear-out}

To stop paying for the resources you created:

1. Open the `wordpress.tf` configuration file and delete from it the description of the infrastructure you created.
1. Apply the changes:

   {% include [terraform-validate-plan-apply](../../_tutorials_includes/terraform-validate-plan-apply.md) %}

