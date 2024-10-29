---
title: Как получить список поддерживаемых языков в {{ translate-full-name }}
description: Из статьи вы узнаете, как получить список поддерживаемых языков в {{ translate-name }}.
---

# Получение списка поддерживаемых языков

## Перед началом работы {#before-you-begin}

{% include [curl](../../_includes/curl.md) %}

{% include [ai-before-beginning](../../_includes/translate/ai-before-beginning.md) %}

{% include [bash-windows-note-single](../../_includes/translate/bash-windows-note-single.md) %}

## Получить список поддерживаемых языков {#get-languages}

Получите список [поддерживаемых языков](../concepts/supported-languages.md) с помощью метода [listLanguages](../api-ref/Translation/listLanguages):

{% list tabs group=programming_language %}

- Bash {#bash}

    ```bash
    export FOLDER_ID=<идентификатор_каталога>
    export IAM_TOKEN=<IAM-токен>
    curl \
      --request POST \
      --header "Content-Type: application/json" \
      --header "Authorization: Bearer ${IAM_TOKEN}" \
      --data "{\"folderId\": \"${FOLDER_ID}\"}" \
      "https://translate.{{ api-host }}/translate/v2/languages"
    ```

    Где:

    * `FOLDER_ID` — идентификатор каталога, полученный [перед началом работы](#before-begin).
    * `IAM_TOKEN` — IAM-токен, полученный [перед началом работы](#before-begin).

    Ответ будет содержать список языков с названиями на соответствующем языке:

    ```json
    {
        "languages": [
            {
            "code": "az",
            "name": "azərbaycan"
            },
            {
            "code": "sq",
            "name": "shqip"
            },
            {
            "code": "am",
            "name": "አማርኛ"
            },
            {
            "code": "en",
            "name": "English"
            },
            ...
        ]
    }
    ```

{% endlist %}