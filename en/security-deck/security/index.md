---
title: Access management in {{ sd-full-name }}
description: Managing access permissions in {{ sd-full-name }} information security management service. For access to {{ sd-name }} resources, assign to the user the required roles from the list below.
---

# Access management in {{ sd-full-name }}

{{ yandex-cloud }} users can only perform operations on resources that are allowed by the roles assigned to them. Until roles are assigned, the user cannot perform any operations.

For access to {{ sd-name }} resources, assign the required roles from the list below to a Yandex account, [service account](../../iam/concepts/users/service-accounts.md), [federated users](../../iam/concepts/federations.md), [user group](../../organization/operations/manage-groups.md), or [system group](../../iam/concepts/access-control/system-group.md). Currently, a role can only be assigned for a parent resource (folder or cloud). Roles are inherited by nested resources.

{% note info %}

For more information about role inheritance, see [Inheritance of access permissions](../../resource-manager/concepts/resources-hierarchy.md#access-rights-inheritance) in the {{ resmgr-name }} documentation.

{% endnote %}

## Which roles exist in the service {#roles-list}

In {{ sd-name }}, you can manage access using both service and primitive roles.

### Service roles {#service-roles}

{{ yandex-cloud }} supports a separate list of roles for each {{ sd-name }} module. For more information, see:

* [Roles for analyzing Access Transparency data](./access-transparency-roles.md).
* [Roles for Data Security Posture Management (DSPM)](./dspm-roles.md).
* [Roles for Cloud Infrastructure Entitlement Management (CIEM)](./ciem-roles.md).

### Primitive roles {#primitive-roles}

{% include [roles-primitive](../../_includes/roles-primitive.md) %}

{% include [primitive-roles-footnote](../../_includes/primitive-roles-footnote.md) %}

## See also {#see-also}

[Hierarchy of {{ yandex-cloud }}](../../resource-manager/concepts/resources-hierarchy.md) resources