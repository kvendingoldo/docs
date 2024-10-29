{% list tabs group=instructions %}

- {{ org-name }} interface {#cloud-org}

  1. Go to [{{ org-full-name }}]({{ link-org-main }}).
  1. In the left-hand panel, select **{{ ui-key.yacloud_org.pages.groups }}** ![icon-services](../../_assets/console-icons/persons.svg) and click the line with the [group](../../organization/concepts/groups.md) name.
  1. Go to the **{{ ui-key.yacloud_org.entity.group.title_tab-members }}** tab.
  1. Click **{{ ui-key.yacloud_org.entity.group.action_add-member }}**.
  1. In the **{{ ui-key.yacloud_org.component.subject-select-dialog.title_dialog }}** window, select users from the list or search by user. You can also add [service accounts](../../iam/concepts/users/service-accounts.md) to a group.
  1. Click **{{ ui-key.yacloud_org.component.subject-select-dialog.action_apply }}**.

- CLI {#cli}

  {% include [cli-install](../../_includes/cli-install.md) %}

  {% include [default-catalogue](../../_includes/default-catalogue.md) %}

  1. See the description of the command for adding members to the {{ org-name }} user group:

      ```bash
      yc organization-manager group add-members --help
      ```

  1. To add members to a user group, run this command:

      ```bash
      yc organization-manager group add-members \
        --name <group_name> \
        --organization-id <organization_ID> \
        --subject-id <member_ID>
      ```

      Where:

      * `--name`: User group name. This is a required parameter.
      * `--organization-id`: Organization ID.
      * `--subject-id`: ID of the member to add to the group.

- {{ TF }} {#tf}

  {% include [terraform-definition](../../_tutorials/_tutorials_includes/terraform-definition.md) %}

  {% include [terraform-install](../../_includes/terraform-install.md) %}

  1. In the configuration file, describe the new [group](../../organization/concepts/groups.md) members:

     ```hcl
     resource "yandex_organizationmanager_group_membership" "group-members" {
        group_id = "<group_ID>"
        members  = [
          "<member_1_ID>",
          "<member_2_ID>"
        ]
     }
     ```

     Where:

     * `group_id`: ID of the group to add the member to.
     * `members`: [IDs](../../organization/operations/users-get.md) of the members to add to the group.
  1. Create resources:

     {% include [terraform-validate-plan-apply](../../_tutorials/_tutorials_includes/terraform-validate-plan-apply.md) %}

     {{ TF }} will create all the required resources. You can check the new resources and their configuration using the [management console]({{ link-console-main }}) or this [CLI](../../cli/) command:

     ```bash
     yc organization-manager group list-memebers \
       --name <group_name> \
       --organization-id <organization_ID>
     ```

- API {#api}

    Use the [Group.updateMembers](../../organization/api-ref/Group/updateMembers.md) REST API method for the [Group](../../organization/api-ref/Group/index.md) resource or the [GroupService/UpdateMembers](../../organization/api-ref/grpc/Group/updateMembers.md) gRPC API call.

{% endlist %}