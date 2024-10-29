# Модели {{ yagpt-full-name }}

{{ yagpt-full-name }} предоставляет доступ к большим текстовым моделям:

* стандартной {{ gpt-lite }}, подходящей для решения задач в режиме реального времени;
* большой {{ gpt-pro }}, которая дает более точные ответы на сложные запросы.

Если стандартных моделей вам недостаточно, вы можете [дообучить](../../tutorials/yagpt-tuning) {{ gpt-pro }} в сервисе [{{ ml-platform-full-name }}]({{ link-datasphere-main }}), чтобы модель точнее отвечала на ваши запросы.

Чтобы [обратиться](../../operations/yandexgpt/create-prompt.md) к модели по API, в параметре `modelUri` укажите ее [URI](https://ru.wikipedia.org/wiki/URI), содержащий [идентификатор каталога](../../../resource-manager/operations/folder/get-id.md). Сегменты `/latest`, `/rc` и `/deprecated` указывают версию модели. По умолчанию используется сегмент `/latest`.

## Модели генерации {{ yagpt-full-name }} {#yandexgpt-generation}

{% note info %}

При обновлении моделей поколения {{ yagpt-name }}, доступные в разных ветках (сегменты `/latest`, `/rc` и `/deprecated`), могут меняться.

{% endnote %}

#|
|| **Модель** | **URI** | **Поколение {{ yagpt-name }}** | **[Режимы работы](../index.md#working-mode)** ||
|| **{{ gpt-lite }}** | `gpt://<идентификатор_каталога>/yandexgpt-lite/deprecated`
`gpt://<идентификатор_каталога>/yandexgpt-lite/latest` 
`gpt://<идентификатор_каталога>/yandexgpt-lite/rc`	| 3</br>3</br>4 |  Асинхронный, синхронный ||
|| **{{ gpt-pro }}** | `gpt://<идентификатор_каталога>/yandexgpt/deprcecated` 
`gpt://<идентификатор_каталога>/yandexgpt/latest` 
`gpt://<идентификатор_каталога>/yandexgpt/rc` | 3</br>3</br>4  | Асинхронный, синхронный ||
|| **{{ gpt-pro }} 32k** | `gpt://<идентификатор_каталога>/yandexgpt-32k/rc` | 4 | Синхронный^1^ ||
|| **Модель, дообученная в {{ ml-platform-full-name }}** | `ds://<идентификатор_каталога>/<идентификатор_дообученной_модели>` | 3 | Асинхронный, синхронный ||
|#

Модифицированные модели делят [квоты](../limits.md#quotas) на использование со своими базовыми моделями.

^1^ Модель **{{ gpt-pro }} 32k** обладает расширенным контекстом и создана специально для обработки больших текстов в синхронном режиме. В асинхронном режиме модель **{{ gpt-pro }}** поддерживает тот же объем контекста. 

{% include [release-cycle](../../../_includes/foundation-models/release-cycle.md) %}

## Возможности дообучения {#tuning-abilities}

{% include [tuning-abilities](../../../_includes/foundation-models/yandexgpt/tuning-abilities.md) %}
