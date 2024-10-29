# Управление доступом в {{ yq-name }}

Для управления правами доступа в {{ yq-name }} используются [роли](../../iam/concepts/access-control/roles.md).

Пользователь {{ yandex-cloud }} может выполнять только те операции над ресурсами, которые разрешены назначенными ему ролями. Пока у пользователя нет никаких ролей, почти все операции ему запрещены.

Чтобы разрешить доступ к ресурсам сервиса {{ yq-full-name }}, назначьте аккаунту на Яндексе, [сервисному аккаунту](../../iam/concepts/users/service-accounts.md), [федеративным пользователям](../../iam/concepts/federations.md), [группе пользователей](../../organization/operations/manage-groups.md), [системной группе](../../iam/concepts/access-control/system-group.md) или [публичной группе](../../iam/concepts/access-control/public-group.md) нужные роли из приведенного ниже списка. На данный момент роль может быть назначена только на родительский ресурс (каталог или облако), роли которого наследуются вложенными ресурсами.

Назначать роли на ресурс могут пользователи, у которых на этот ресурс есть роль `yq.admin` или одна из следующих ролей:

{% include [roles-list](../../_includes/iam/roles-list.md) %}

{% note info %}

Подробнее о наследовании ролей читайте в разделе [{#T}](../../resource-manager/concepts/resources-hierarchy.md#access-rights-inheritance) документации сервиса {{ resmgr-full-name }}.

{% endnote %}

## Назначение ролей {#grant-roles}

Чтобы назначить пользователю роль:

{% include [grant-role-console](../../_includes/grant-role-console.md) %}

## Какие роли действуют в сервисе {#roles-list}

Управлять доступом к объектам {{ yq-name }} можно как с помощью сервисных, так и с помощью примитивных ролей. На диаграмме показано, какие роли есть в сервисе и как они наследуют разрешения друг друга. Например, в `editor` входят все разрешения `viewer`. После диаграммы дано описание каждой роли.

<center>

![image](../../_assets/query/service-roles-hierarchy.svg)

</center>

Ниже перечислены все роли, которые учитываются при проверке прав доступа в сервисе {{ yq-name }}.

### Сервисные роли {#service-roles}

#### yq.auditor {#query-auditor}

{% include [query.auditor](../../_roles/yq/auditor.md) %}

#### yq.viewer {#query-viewer}

{% include [query.viewer](../../_roles/yq/viewer.md) %}

#### yq.editor {#query-editor}

{% include [query.editor](../../_roles/yq/editor.md) %}

#### yq.admin {#query-admin}

{% include [query.admin](../../_roles/yq/admin.md) %}

#### yq.invoker {#query-invoker}

{% include [query.invoker](../../_roles/yq/invoker.md) %}

### Примитивные роли {#primitive-roles}

#### {{ roles-viewer }}

Пользователь с ролью `{{ roles-viewer }}` может просматривать информацию о ресурсах, например, о запусках запроса.

#### {{ roles-editor }}

Пользователь с ролью `{{ roles-editor }}` может управлять любыми ресурсами, например, создать или удалить запрос. Роль `{{ roles-editor }}` включает в себя все разрешения роли `{{ roles-viewer }}`.

#### {{ roles-admin }}

Пользователь с ролью `{{ roles-admin }}` может управлять правами доступа к ресурсам, например, разрешить другим пользователям создавать запросы. Роль `{{ roles-admin }}` включает в себя все разрешения роли `{{ roles-editor }}`.
