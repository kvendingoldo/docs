# Как настроить Cleanup Policy, когда закончилось место


## Описание сценария {#case-description}

Необходимо настроить очистку, потому что закончилось место.

## Решение {#case-resolution}

Для очистки места нужно настроить Cleanup Policy. Про включение — подробнее [здесь](https://docs.gitlab.com/ee/user/packages/container_registry/reduce_container_registry_storage.html#enable-the-cleanup-policy). 

Вам понадобится:

1. [Выставить настройки](https://docs.gitlab.com/ee/api/settings.html#get-current-application-settings).
1. Подставить нужные параметры и [применить настройки](https://docs.gitlab.com/ee/api/settings.html#change-application-settings).

{% note info %}

По умолчанию Cleanup Policy вызывается каждые 12 часов. В качестве разового решения можно попробовать удалить ненужные теги вручную, в том числе из интерфейса {{ mgl-name }}.

{% endnote %}