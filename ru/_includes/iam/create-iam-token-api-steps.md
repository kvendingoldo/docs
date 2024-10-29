1. [Войдите]({{ link-passport-login }}) в ваш аккаунт на Яндексе.
1. Получите [OAuth-токен](../../iam/concepts/authorization/oauth-token.md) в сервисе Яндекс.OAuth. Для этого перейдите по [ссылке]({{ link-cloud-oauth }}), нажмите **Разрешить** и скопируйте полученный OAuth-токен.
1. Обменяйте OAuth-токен на [IAM-токен](../../iam/concepts/authorization/iam-token.md):

    * с помощью [curl](https://curl.haxx.se) в Bash:

        ```bash
        curl \
          --request POST \
          --data '{"yandexPassportOauthToken":"<OAuth-токен>"}' \
          https://iam.{{ api-host }}/iam/v1/tokens
        ```
    * с помощью встроенной функции в PowerShell:

        ```powershell
        $yandexPassportOauthToken = "<OAuth-токен>"
        $Body = @{ yandexPassportOauthToken = "$yandexPassportOauthToken" } | ConvertTo-Json -Compress
        Invoke-RestMethod -Method 'POST' -Uri 'https://iam.{{ api-host }}/iam/v1/tokens' -Body $Body -ContentType 'Application/json' | Select-Object -ExpandProperty iamToken
        ```