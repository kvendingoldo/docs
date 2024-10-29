## Представление аудитного лога {#log-name}

В зависимости от [объекта назначения](../../audit-trails/concepts/trail.md#target) — бакет или лог-группа — изменяется структура и содержимое сообщения, в составе которого {{ at-name }} передает объекту назначения аудитные логи:
* для бакета — файл, в котором находится массив [JSON-объектов](#scheme) аудитного лога;
* для лог-группы — сообщение, в котором находится только один JSON-объект аудитного лога.

### Файл аудитного лога в бакете {#log-file-name}

Шаблон полного имени файла аудитного лога в бакете:

`<префикс_объекта>/<идентификатор_трейла>/<год>/<месяц>/<имя_файла.json>`

### Запись в лог-группе {#logging-group-name}

Значения записей в лог-группе:
* **{{ ui-key.yacloud.logging.column_header-time }}** — значение поля `event_time` события.
* **JSON** — JSON-объект события.
* **{{ ui-key.yacloud.logging.column_header-level }}** — вычисляется в зависимости от значения `event_status` события:
  * `ERROR` — для значения `ERROR`;
  * `WARN` — для значения `CANCELLED`;
  * `INFO` — в остальных случаях.
* **{{ ui-key.yacloud.logging.column_header-message }}** — содержит значения полей `event_status`, `event_type`, `subject_name`, `cloud_name`, `resource_name`.

{% include [logging-dublicate-events](../../_includes/audit-trails/logging-dublicate-events.md) %}