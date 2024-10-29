Запишите IAM-токен в переменную с помощью CLI и используйте токен в других запросах из командной строки. Пример запроса на получение списка облаков:

{% list tabs group=programming_language %}

- Bash {#bash}

  ```bash
  export IAM_TOKEN=`yc iam create-token`
  curl \
    --request GET \
    --header "Authorization: Bearer ${IAM_TOKEN}" \
    https://resource-manager.{{ api-host }}/resource-manager/v1/clouds
  ```

- PowerShell {#powershell}

  ```powershell
  $IAM_TOKEN=yc iam create-token
  curl.exe \
    --request GET \
    --header "Authorization: Bearer $IAM_TOKEN" `
    https://resource-manager.{{ api-host }}/resource-manager/v1/clouds
  ```

{% endlist %}
