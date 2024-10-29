# Создать триггер для {{ objstorage-name }}, который вызывает функцию {{ sf-name }}

Создайте [триггер для {{ objstorage-name }}](../../concepts/trigger/os-trigger.md), который будет вызывать [функцию](../../concepts/function.md) {{ sf-name }} при создании, перемещении или удалении [объекта](../../../storage/concepts/object.md) в бакете.

## Перед началом работы {#before-you-begin}

{% include [trigger-before-you-begin](../../../_includes/functions/trigger-before-you-begin.md) %}

* [Бакет](../../../storage/concepts/bucket.md), при событиях с объектами в котором триггер будет запускаться. Если у вас нет бакета, [создайте его](../../../storage/operations/buckets/create.md) с ограниченным доступом.

## Создать триггер {#trigger-create}

{% include [trigger-time](../../../_includes/functions/trigger-time.md) %}

{% list tabs group=instructions %}

- Консоль управления {#console}

    1. В [консоли управления]({{ link-console-main }}) перейдите в каталог, в котором хотите создать триггер.

    1. Выберите сервис **{{ ui-key.yacloud.iam.folder.dashboard.label_serverless-functions }}**.

    1. На панели слева выберите ![image](../../../_assets/console-icons/gear-play.svg) **{{ ui-key.yacloud.serverless-functions.switch_list-triggers }}**.

    1. Нажмите кнопку **{{ ui-key.yacloud.serverless-functions.triggers.list.button_create }}**.

    1. В блоке **{{ ui-key.yacloud.serverless-functions.triggers.form.section_base }}**:

        * Введите имя и описание триггера.
        * В поле **{{ ui-key.yacloud.serverless-functions.triggers.form.field_type }}** выберите **{{ ui-key.yacloud.serverless-functions.triggers.form.label_storage }}**.
        * В поле **{{ ui-key.yacloud.serverless-functions.triggers.form.field_invoke }}** выберите **{{ ui-key.yacloud.serverless-functions.triggers.form.label_function }}**.

    1. В блоке **{{ ui-key.yacloud.serverless-functions.triggers.form.section_storage }}**:

        * В поле **{{ ui-key.yacloud.serverless-functions.triggers.form.field_bucket }}** выберите бакет, для событий с объектами которого хотите создать триггер.
        * В поле **{{ ui-key.yacloud.serverless-functions.triggers.form.field_event-types }}** выберите [события](../../concepts/trigger/os-trigger.md#event), после наступления которых триггер будет запускаться.
        * (Опционально) В поле **{{ ui-key.yacloud.serverless-functions.triggers.form.field_prefix }}** введите [префикс](../../concepts/trigger/os-trigger.md#filter) для фильтрации.
        * (Опционально) В поле **{{ ui-key.yacloud.serverless-functions.triggers.form.field_suffix }}** введите [суффикс](../../concepts/trigger/os-trigger.md#filter) для фильтрации.

    1. В блоке **{{ ui-key.yacloud.serverless-functions.triggers.form.section_batch-settings }}** укажите:

        {% include [batch-settings](../../../_includes/functions/batch-settings.md) %}

        {% include [batch-events](../../../_includes/functions/batch-events.md) %}

    1. В блоке **{{ ui-key.yacloud.serverless-functions.triggers.form.section_function }}** выберите функцию и укажите:

        {% include [function-settings](../../../_includes/functions/function-settings.md) %}

    1. (Опционально) В блоке **{{ ui-key.yacloud.serverless-functions.triggers.form.section_function-retry }}**:

        {% include [repeat-request.md](../../../_includes/functions/repeat-request.md) %}

    1. (Опционально) В блоке **{{ ui-key.yacloud.serverless-functions.triggers.form.section_dlq }}** выберите очередь Dead Letter Queue и сервисный аккаунт с правами на запись в нее.

    1. Нажмите кнопку **{{ ui-key.yacloud.serverless-functions.triggers.form.button_create-trigger }}**.

- CLI {#cli}

    {% include [cli-install](../../../_includes/cli-install.md) %}

    {% include [default-catalogue](../../../_includes/default-catalogue.md) %}

    Чтобы создать триггер, который вызывает функцию, выполните команду:

    ```bash
    yc serverless trigger create object-storage \
      --name <имя_триггера> \
      --bucket-id <идентификатор_бакета> \
      --prefix '<префикс_ключа_объекта>' \
      --suffix '<суффикс_ключа_объекта>' \
      --events 'create-object','delete-object','update-object' \
      --batch-size <размер_группы_событий> \
      --batch-cutoff <максимальное_время_ожидания> \
      --invoke-function-id <идентификатор_функции> \
      --invoke-function-service-account-id <идентификатор_сервисного_аккаунта> \
      --retry-attempts <количество_повторных_вызовов> \
      --retry-interval <интервал_между_повторными_вызовами> \
      --dlq-queue-id <идентификатор_очереди_Dead_Letter_Queue> \
      --dlq-service-account-id <идентификатор_сервисного_аккаунта>
    ```

    Где:

    * `--name` — имя триггера.
    * `--bucket-id` — идентификатор бакета.
    * `--prefix` — [префикс](../../concepts/trigger/os-trigger.md#filter) ключа объекта в бакете. Необязательный параметр. Используется для фильтрации.
    * `--suffix` — [суффикс](../../concepts/trigger/os-trigger.md#filter) ключа объекта в бакете. Необязательный параметр. Используется для фильтрации.
    * `--events` — [события](../../concepts/trigger/os-trigger.md#event), после наступления которых триггер запускается.

    {% include [batch-settings-events](../../../_includes/functions/batch-settings-events.md) %}

    {% include [trigger-cli-param](../../../_includes/functions/trigger-cli-param.md) %}

    Результат:

    ```text
    id: a1s92agr8mpg********
    folder_id: b1g88tflru0e********
    created_at: "2019-12-18T09:47:50.079103Z"
    name: os-trigger
    rule:
      object_storage:
        event_type:
        - OBJECT_STORAGE_EVENT_TYPE_CREATE_OBJECT
        - OBJECT_STORAGE_EVENT_TYPE_DELETE_OBJECT
        - OBJECT_STORAGE_EVENT_TYPE_UPDATE_OBJECT
        bucket_id: s3-for-trigger
        prefix: dev
        suffix: 12.jpg
        batch_settings:
          size: "3"
          cutoff: 20s
        invoke_function:
          function_id: d4eofc7n0m03********
          function_tag: $latest
          service_account_id: aje3932acd0c********
          retry_settings:
            retry_attempts: "1"
            interval: 10s
          dead_letter_queue:
            queue-id: yrn:yc:ymq:{{ region-id }}:aoek49ghmknn********:dlq
            service-account-id: aje3932acd0c********
    status: ACTIVE
    ```

- {{ TF }} {#tf}

  {% include [terraform-definition](../../../_tutorials/_tutorials_includes/terraform-definition.md) %}

  {% include [terraform-install](../../../_includes/terraform-install.md) %}

  Чтобы создать триггер для {{ objstorage-name }}:

  1. Опишите в конфигурационном файле {{ TF }} параметры ресурсов, которые необходимо создать:

     ```
     resource "yandex_function_trigger" "my_trigger" {
       name        = "<имя_триггера>"
       description = "<описание_триггера>"
       function {
         id                 = "<идентификатор_функции>"
         service_account_id = "<идентификатор_сервисного_аккаунта>"
         retry_attempts     = "<количество_повторных_вызовов>"
         retry_interval     = "<интервал_между_повторными_вызовами>"
       }
       object_storage {
         bucket_id    = "<идентификатор_бакета>"
         prefix       = "<префикс_ключа_объекта>"
         suffix       = "<суффикс_ключа_объекта>"
         create       = true
         update       = true
         delete       = true
         batch_cutoff = "<максимальное_время_ожидания>"
         batch_size   = "<размер_группы_событий>"
       }
       dlq {
         queue_id           = "<идентификатор_очереди_Dead_Letter_Queue>"
         service_account_id = "<идентификатор_сервисного_аккаунта>"
       }
     }
     ```

     Где:

     {% include [tf-function-params](../../../_includes/functions/tf-function-params.md) %}

     * `object_storage` — параметры триггера:

        * `bucket_id` — идентификатор бакета.
        * `prefix` — [префикс](../../concepts/trigger/os-trigger.md#filter) ключа объекта в бакете. Необязательный параметр. Используется для фильтрации.
        * `suffix` — [суффикс](../../concepts/trigger/os-trigger.md#filter) ключа объекта в бакете. Необязательный параметр. Используется для фильтрации.
        * [События](../../concepts/trigger/os-trigger.md#event), после наступления которых триггер запускается:

            * `create` — триггер вызовет функцию при создании нового объекта в хранилище. Принимает значения `true` или `false`.
            * `update` — триггер вызовет функцию при обновлении объекта в хранилище. Принимает значения `true` или `false`.
            * `delete` — триггер вызовет функцию при удалении объекта из хранилища. Принимает значения `true` или `false`.
        
        {% include [tf-batch-params-events](../../../_includes/functions/tf-batch-params-events.md) %}
        
     {% include [tf-dlq-params](../../../_includes/serverless-containers/tf-dlq-params.md) %}

     Более подробную информацию о параметрах ресурса `yandex_function_trigger` см. в [документации провайдера]({{ tf-provider-resources-link }}/function_trigger).

  1. Создайте ресурсы:

     {% include [terraform-validate-plan-apply](../../../_tutorials/_tutorials_includes/terraform-validate-plan-apply.md) %}

     {% include [terraform-check-result](../../../_tutorials/_tutorials_includes/terraform-check-result.md) %}

     ```bash
     yc serverless trigger list
     ```

- API {#api}

  Чтобы создать триггер для {{ objstorage-name }}, воспользуйтесь методом REST API [create](../../triggers/api-ref/Trigger/create.md) для ресурса [Trigger](../../triggers/api-ref/Trigger/index.md) или вызовом gRPC API [TriggerService/Create](../../triggers/api-ref/grpc/Trigger/create.md).

{% endlist %}

## Проверить результат {#check-result}

{% include [check-result](../../../_includes/functions/check-result.md) %}

## См. также {#see-also}

* [{#T}](../../../serverless-containers/operations/os-trigger-create.md)
* [{#T}](../../../api-gateway/operations/trigger/os-trigger-create.md)
