# Getting information about a service account

You can get information about a service account: its name and ID, creation and last authentication dates, and its roles in the folder.

{% list tabs group=instructions %}

- Management console {#console}

  1. In the [management console]({{ link-console-main }}), navigate to the folder the service account belongs to.
  1. At the top of the screen, go to the **{{ ui-key.yacloud.iam.folder.switch_service-accounts }}** tab.
  1. Choose a service account and click the row with its name.
  1. The **{{ ui-key.yacloud.iam.folder.service-account.overview.label_title }}** page will list the service account's parameters:

     * **{{ ui-key.yacloud.iam.folder.service-account.overview.label_id }}** of the service account as a string in `aje9sb6ffd2u********` format.
     * **{{ ui-key.yacloud.iam.folder.service-accounts.column_name }}**.
     * **{{ ui-key.yacloud.iam.folder.service-accounts.column_date }}**.
     * **{{ ui-key.yacloud.iam.folder.service-accounts.column_last-auth }}**.
     * **{{ ui-key.yacloud.iam.folder.service-accounts.column_roles }}**.

- CLI {#cli}

  {% include [cli-install](../../../_includes/cli-install.md) %}

  {% include [default-catalogue](../../../_includes/default-catalogue.md) %}

  Get a list of service accounts in the default folder:

  ```bash
  yc iam service-account list
  ```

  Result:

  ```
  +----------------------+------------------+-------------------------------+
  |          ID          |       NAME       |          DESCRIPTION          |
  +----------------------+------------------+-------------------------------+
  | aje6o61dvog2******** | my-robot         |                               |
  | aje9sda1ufvq******** | account_name     | account_description           |
  +----------------------+------------------+-------------------------------+
  ```

  Get information about a service account using the `get` command:

  ```bash
  yc iam service-account get <service_account_ID>
  ```
  
  Result:

  ```
  id: aje6o61dvog2********
  folder_id: jbmsjns93hj8********
  created_at: "2024-09-09T20:15:19Z"
  name: service-account
  last_authenticated_at: "2024-09-19T18:05:06Z"
  ```

  Where:

  * `id`: Service account ID.
  * `folder_id`: Folder ID.
  * `created_at`: Service account creation date and time.
  * `name: service-account`: Service account name.
  * `last_authenticated_at`: Last authentication date and time.

- API {#api}

  1. [Find out the ID of the folder](../../../resource-manager/operations/folder/get-id.md) where the service account was created.
  1. Get information about the service accounts in the folder using the [list](../../api-ref/ServiceAccount/list.md) REST API method for the [ServiceAccount](../../api-ref/ServiceAccount/index.md) resource:

      ```bash
      export FOLDER_ID=b1gvmob95yys********
      export IAM_TOKEN=CggaATEVAgA...
      curl -H "Authorization: Bearer ${IAM_TOKEN}" \
        "https://iam.{{ api-host }}/iam/v1/serviceAccounts?folderId=${FOLDER_ID}"

      {
       "serviceAccounts": [
        {
         "id": "ajebqtreob2d********",
         "folderId": "b1gvmob95yys********",
         "createdAt": "2018-10-18T13:42:40Z",
         "name": "my-robot",
         "description": "my description"
        }
       ]
      }
      ```

      You can also get information about the service accounts in the folder using the [ServiceAccountService/List](../../api-ref/grpc/ServiceAccount/list.md) gRPC API call.

{% endlist %}
