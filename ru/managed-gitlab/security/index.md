---
title: Управление доступом в {{ mgl-full-name }}
description: Управление доступом в веб-инструменте жизненного цикла DevOps с открытым исходным кодом — {{ mgl-full-name }}. В разделе описано, на какие ресурсы можно назначить роль, какие роли действуют в сервисе, какие роли необходимы для того или иного действия.
---

# Управление доступом в {{ mgl-name }}

В этом разделе вы узнаете:
* [на какие ресурсы можно назначить роль](#resources);
* [какие роли действуют в сервисе](#roles-list);
* [какие роли необходимы](#required-roles) для того или иного действия.


Для использования сервиса необходимо авторизоваться в консоли управления с [аккаунтом на Яндексе](../../iam/concepts/users/accounts.md#passport) или с [федеративным аккаунтом](../../iam/concepts/users/accounts.md#saml-federation).


{% include [about-access-management](../../_includes/iam/about-access-management.md) %}

Назначать роли на ресурс могут пользователи, у которых на этот ресурс есть роль `gitlab.admin` или одна из следующих ролей:

{% include [roles-list](../../_includes/iam/roles-list.md) %}

## На какие ресурсы можно назначить роль {#resources}

Роль можно назначить на организацию, [облако](../../resource-manager/concepts/resources-hierarchy.md#cloud) или [каталог](../../resource-manager/concepts/resources-hierarchy.md#folder). Роли автоматически наследуются на вложенные ресурсы.

## Какие роли действуют в сервисе {#roles-list}

### Сервисные роли {#service-roles}

#### gitlab.auditor {#gitlab-auditor}

{% include [gitlab.auditor](../../_roles/gitlab/auditor.md) %}

#### gitlab.viewer {#gitlab-viewer}

{% include [gitlab.viewer](../../_roles/gitlab/viewer.md) %}

#### gitlab.editor {#gitlab-editor}

{% include [gitlab.editor](../../_roles/gitlab/editor.md) %}

#### gitlab.admin {#gitlab-admin}

{% include [gitlab.admin](../../_roles/gitlab/admin.md) %}

### Примитивные роли {#primitive-roles}

{% include [roles-primitive](../../_includes/roles-primitive.md) %}

{% include [primitive-roles-footnote](../../_includes/primitive-roles-footnote.md) %}

## Какие роли необходимы {#required-roles}

Чтобы пользоваться сервисом, необходима роль [{{ roles.gitlab.editor }} или выше](../../iam/concepts/access-control/roles.md) на каталог, в котором создаются проекты. Роль `{{ roles.gitlab.viewer }}` позволит только просматривать список проектов и содержимое файлов, которые были загружены.

Чтобы создать инстанс {{ mgl-name }}, нужна роль [{{ roles-vpc-user }}](../../vpc/security/index.md#vpc-user) и роль `{{ roles.gitlab.editor }}` или выше.

Вы всегда можете назначить роль, которая дает более широкие разрешения. Например, назначить `{{ roles.gitlab.admin }}` вместо `{{ roles.gitlab.editor }}`.


## Что дальше {#whats-next}

* [Как назначить роль](../../iam/operations/roles/grant.md).
* [Как отозвать роль](../../iam/operations/roles/revoke.md).
* [Подробнее об управлении доступом в {{ yandex-cloud }}](../../iam/concepts/access-control/index.md).
* [Подробнее о наследовании ролей](../../resource-manager/concepts/resources-hierarchy.md#access-rights-inheritance).

