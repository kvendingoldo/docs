To create a trigger, you need:

* A function that the trigger will invoke. If you do not have a function:

   * [Create a function](../../functions/operations/function/function-create.md).
   * [Create a function version](../../functions/operations/function/version-manage.md).

* (Optional) A [dead-letter queue](../../functions/concepts/dlq.md) where messages that could not be processed by a function will be redirected. If you do not have a queue, [create one](../../message-queue/operations/message-queue-new-queue.md).

* [Service accounts](../../iam/concepts/users/service-accounts.md) with permissions to invoke the function and (optionally) write messages to the dead-letter queue. You can use the same service account or different ones. If you do not have a service account, [create one](../../iam/operations/sa/create.md).
