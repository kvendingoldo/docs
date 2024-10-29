{% list tabs group=instructions %}

- Management console {#console}

   1. In the [management console]({{ link-console-main }}), go to the folder where you want to view a list of triggers.
   1. Open **{{ ui-key.yacloud.iam.folder.dashboard.label_serverless-containers }}**.
   1. In the left-hand panel, select ![image](../../_assets/console-icons/gear-play.svg) **{{ ui-key.yacloud.serverless-functions.switch_list-triggers }}**.

- CLI {#cli}

   {% include [cli-install](../cli-install.md) %}

   {% include [default-catalogue](../default-catalogue.md) %}

   Get a list of triggers:

   ```bash
   yc serverless trigger list
   ```

   Result:

   ```text
   +----------------------+------------+----------------------+
   |          ID          |    NAME    |      FOLDER ID       |
   +----------------------+------------+----------------------+
   | dd0gj5tsj2p3******** | my-trigger | aoek49ghmki7******** |
   +----------------------+------------+----------------------+
   ```

- API {#api}

   To get a list of triggers, use the [list](../../serverless-containers/triggers/api-ref/Trigger/list.md) REST API method for the [Trigger](../../serverless-containers/triggers/api-ref/Trigger/index.md) resource or the [TriggerService/List](../../serverless-containers/triggers/api-ref/grpc/Trigger/list.md) gRPC API call.

{% endlist %}
