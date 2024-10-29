---
title: Как добавить поле задачи в {{ tracker-full-name }}
description: Из статьи вы узнаете, как добавить поле задачи в {{ tracker-name }}. Поля могут быть глобальными и локальными. Вы можете воспользоваться набором готовых полей, или создать свои.
---

# Добавить поле задачи

## Стандартные поля задач {#default-fields}

По умолчанию в {{ tracker-name }} доступны наиболее популярные поля (параметры) задач. Список существующих полей можно посмотреть на странице [Настройки {{ tracker-name }}]({{ link-admin-fields }}).

Если нужного вам параметра среди них нет, вы можете [создать новое поле в вашей очереди](#section_local_field). Если нужно добавить поле, которое будет доступно во всех очередях {{ tracker-name }}, администратор может [создать глобальное поле](#section_global_field).

Поле задачи | Описание
----- | -----
**{{ ui-key.startrek-backend.fields.issue.fields.system }}**  
QA-инженер | Пользователь, который назначен тестировать задачу.
{{ ui-key.startrek-backend.fields.issue.author-key-value }} | Пользователь, который создал задачу.
{{ ui-key.startrek-backend.fields.issue.possibleSpam }} | Признак спама для задач, созданных через сервисы, с которыми настроена [интеграция](../manager/queue-mail.md).
{{ ui-key.startrek-backend.fields.issue.end-key-value }} | Дата окончания работы над задачей. 
{{ ui-key.startrek-backend.fields.issue.start-key-value }} | Дата начала работы над задачей. 
{{ ui-key.startrek-backend.fields.issue.dueDate-key-value }} | Дата, к которой задача должна быть решена.
{{ ui-key.startrek-backend.fields.issue.boards }} | Список досок, на которые добавлена задача.
{{ ui-key.startrek-backend.fields.issue.access }} | Список пользователей, которые имеют доступ к задаче на чтение и редактирование, но не получают уведомлений о ее изменениях.<br/><br/>Правила доступа к задачам зависят от [настроек очереди](../manager/queue-access.md).
{{ ui-key.startrek-backend.fields.issue.summary-key-value }} | Название задачи.
{{ ui-key.startrek-backend.fields.issue.modifier }} | Пользователь, который последним внес изменения в задачу.
{{ ui-key.startrek-backend.fields.issue.assignee-key-value }} | Пользователь, который будет работать над задачей. 
{{ ui-key.startrek-backend.fields.issue.fixVersions-key-value }} | Версия продукта, к которой относится задача. Список доступных [версий](../manager/versions.md) определяется настройками очереди.
{{ ui-key.startrek-backend.fields.issue.key-key-value }} | Уникальный идентификатор задачи в рамках очереди. Создается автоматически.
{{ ui-key.startrek-backend.fields.issue.commentWithoutExternalMessageCount }} | Количество комментариев к задаче, созданных в сервисе {{tracker-name}}.
{{ ui-key.startrek-backend.fields.issue.commentWithExternalMessageCount }} | Количество комментариев к задаче, созданных через [почту](../manager/queue-mail.md).
{{ ui-key.startrek-backend.fields.issue.components-key-value }} | Метки, с помощью которых можно размечать и сортировать задачи внутри очереди.<br/><br/>Список доступных [компонентов](../manager/components.md) определяется настройками очереди.
{{ ui-key.startrek-backend.fields.issue.followers }} | Список пользователей, подписанных на задачу. По умолчанию они имеют доступ на чтение и редактирование, получают уведомления о любых изменениях в задаче.<br/><br/>Правила доступа к задачам зависят от [настроек очереди](../manager/queue-access.md).
{{ ui-key.startrek-backend.fields.issue.affectedVersions-key-value }} | [Версия продукта](../manager/versions.md), к которой относится задача. Список доступных версий определяется настройками очереди.
{{ ui-key.startrek-backend.fields.issue.pendingReplyFrom }} | Список пользователей, которых [призывали в комментариях](comments.md#call-comment). Как только пользователь отвечает на комментарий, его имя исчезает из этого поля.
{{ ui-key.startrek-backend.fields.issue.updated-key-value }} | Дата и время последнего [изменения в задаче](history.md).
{{ ui-key.startrek-backend.fields.issue.description-key-value }} | Постановка задачи: описание того, что требуется сделать.
{{ ui-key.startrek-backend.fields.issue.queue }} | [Ключ очереди](../manager/create-queue.md#key), в которую входит задача.
{{ ui-key.startrek-backend.fields.issue.lastCommentUpdatedAt }} | Дата и время последнего комментария в задаче.
{{ ui-key.startrek-backend.fields.issue.priority-key-value }} | Значение, которое определяет важность задачи. 
{{ ui-key.startrek-backend.roles.role.name.voted-by-follower }} | Список пользователей, проголосовавших в задаче.
{{ ui-key.startrek-backend.fields.issue.votes }} | Количество пользователей, [проголосовавших за задачу](votes.md).
{{ ui-key.startrek-backend.fields.issue.project-key-value }} | Названия [проектов](../manager/project-new.md), к которым относится задача. 
{{ ui-key.startrek-backend.fields.issue.resolved }} | Дата и время, когда была проставлена [резолюция](../manager/create-resolution.md).
{{ ui-key.startrek-backend.fields.issue.followingMaillists }} | Команды и отделы, подписанные на задачу. По умолчанию они имеют доступ к задаче на чтение и редактирование, получают уведомления о любых ее изменениях.<br/><br/>Правила доступа к задачам зависят от [настроек очереди](../manager/queue-access.md).
{{ ui-key.startrek-backend.fields.issue.resolution-key-value }} | Причина закрытия задачи.
{{ ui-key.startrek-backend.fields.issue.resolver }} | Пользователь, который проставил резолюцию в задаче.
{{ ui-key.startrek-backend.fields.issue.created-key-value }} | Дата и время создания задачи.
{{ ui-key.startrek-backend.fields.issue.status-key-value }} | Этап выполнения задачи. Например: «Открыт», «В работе», «Тестируется». Подробнее читайте в разделе [Настроить статусы](../manager/workflow-status-edit.md).
{{ ui-key.startrek-backend.fields.issue.statusStartTime }} | Дата и время изменения статуса задачи.
{{ ui-key.startrek-backend.fields.issue.tags-key-value }} | Текстовые метки, которые облегчают поиск и сортировку задач. Подробнее читайте в разделе [Структурировать задачи](../structure.md).
{{ ui-key.startrek-backend.fields.issue.type-key-value }} | Тип задачи, например: «Новая возможность», «Ошибка», «Улучшение». Подробнее читайте в разделе [{#T}](../manager/add-ticket-type.md).
**{{ ui-key.startrek-backend.fields.issue.fields.timetracking }}** | 
{{ ui-key.startrek-backend.fields.issue.spent-key-value }} | Время, которое исполнитель [потратил на решение задачи](time-spent.md). 
{{ ui-key.startrek-backend.fields.issue.estimation-key-value }} | Время, которое пользователь планирует потратить на решение задачи. Значение в поле уменьшается при указании [затраченного времени](time-spent.md#show-time-spent).
{{ ui-key.startrek-backend.fields.issue.originalEstimation-key-value }} | Первоначальная оценка времени, необходимого для решения задачи. 
**{{ ui-key.startrek-backend.fields.issue.fields.agile }}** | 
{{ ui-key.startrek-backend.fields.issue.storyPoints }} | Трудоемкость задачи в баллах Story Points. Подробнее читайте в разделе [Основные понятия гибкой разработки](../manager/agile.md#dlen_sp).
{{ ui-key.startrek-backend.fields.issue.sprint }} | Название [спринта](../manager/create-agile-sprint.md), к которому относится задача.
**{{ ui-key.startrek-backend.fields.issue.fields.email }}** | 
{{ ui-key.startrek-backend.fields.issue.emailTo }} | Список всех адресов электронной почты, которые пользователь указал в поле **Кому** при отправке письма.
{{ ui-key.startrek-backend.fields.issue.emailCc }} | Адрес электронной почты, который пользователь указал в поле **Копия** при отправке письма.
{{ ui-key.startrek-backend.fields.issue.emailFrom }} | Адрес электронной почты отправителя письма.
{{ ui-key.startrek-backend.fields.issue.emailCreatedBy }} | Адрес электронной почты, на который было отправлено письмо для создания задачи.
**{{ ui-key.startrek-backend.fields.issue.fields.sla }}** | 
{{ ui-key.startrek-backend.fields.issue.sla-key-value }} | Таймер, который отсчитывает время для обработки задач очереди. Например, можно задать время, за которое исполнитель должен отреагировать на новую задачу. Подробнее читайте в разделе [SLA](../sla-head.md).

## Локальные поля {#section_local_field}

Если требуется добавить в задачи новый параметр, которого нет среди существующих в {{ tracker-name }} полей, вы можете добавить локальные поля в вашу очередь.

Локальное поле можно использовать только в задачах той очереди, к которой оно привязано. Преимущество локальных полей в том, что владелец очереди может управлять такими полями без риска повлиять на процессы работы в других очередях. Пользователи, которые работают в других очередях, не будут видеть это поле в своих задачах.

Подробнее о создании и использовании локальных полей читайте в разделе [{#T}](../local-fields.md).

{% note alert %}

Локальные поля временно не поддерживаются в некоторых сценариях работы с задачами. Поддержка этих сценариев будет добавлена позже. Подробнее читайте в разделе [Ограничения локальных полей](../local-fields.md#restrictions). 

{% endnote %}

## Глобальные поля {#section_global_field}

### Добавить глобальное поле {#add_global_field}


{% note alert %}

Добавлять глобальные поля задач может только [администратор](../role-model.md).

{% endnote %}

Чтобы добавить новое поле (параметр) задачи:

1. Убедитесь, что вы авторизованы как [администратор](../role-model.md).

1. На панели слева выберите ![](../../_assets/tracker/svg/admin.svg) **Администрирование** → **Настройка {{ tracker-name }}**.

1. Перейдите на вкладку **Поля**.

1. Нажмите кнопку **Создать поле**.

1. Выберите тип поля и нажмите кнопку **Продолжить**.

1. Задайте параметры нового поля:
    * **Категория**. Все поля в {{ tracker-name }} сгруппированы по категориям. Выберите категорию, которая лучше всего подходит для нового поля.

    * **Название**. Старайтесь давать полям короткие и емкие названия.

    * **Название на английском**. Это название видно в английском интерфейсе {{ tracker-name }}.

    * **Тип чисел** (только для полей типа «Число»).

    * **Значения списка** (только для полей типа «Выпадающий список») — укажите возможные значения и их порядок.

    * **Количество значений в списке** (только для полей типа «Выпадающий список»).
    
    * **Количество сотрудников** (только для полей типа «Список сотрудников»).

1. Нажмите кнопку **Создать**.



### Редактировать глобальное поле {#edit_global_field}

Редактирование параметров глобального поля задачи через веб-интерфейс {{ tracker-name }} не поддерживается. Для этого используйте запросы к {{ api-name }}:

* HTTP-запрос на [изменение названия глобального поля](../concepts/issues/patch-issue-field-name.md);

* HTTP-запрос на [изменение возможных значений глобального поля](../concepts/issues/patch-issue-field-value.md).

### Удалить глобальное поле {#delete_global_field}

Удалить глобальное поле невозможно, но можно скрыть его из интерфейса {{ tracker-name }}. Для этого в теле запроса к {{ api-name }} на [изменение глобального поля](../concepts/issues/patch-issue-field-value.md) для параметра `hidden` установите значение `true`.

Скрытое поле нельзя добавить в задачу на панели справа. 
