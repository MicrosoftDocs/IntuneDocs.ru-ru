---
title: "Создание и развертывание политик защиты приложений"
titleSuffix: Intune Azure preview
description: "Предварительная версия Intune Azure: защита корпоративных данных, используемых в управляемых приложениях, с помощью политик защиты приложений Intune."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f31b2964-e932-4cee-95c4-8d5506966c85
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 607598812a414843f1f33a00670a6a85b6687878
ms.lasthandoff: 02/18/2017

---

# <a name="how-to-create-and-assign-app-protection-policies"></a>Как создать и назначить политики защиты приложений

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

**Если вы не вошли в предварительную версию службы Intune на портале Azure **, в этой статье объясняется, как [создать политику защиты приложения](https://docs.microsoft.com/en-us/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune) в консоли классической версии Intune.

Политики защиты приложений могут применяться к приложениям на устройствах, которыми управляет или не управляет Intune. Подробное описание использования политик защиты приложений и сценариев, поддерживаемых политиками защиты приложения Intune, см. в статье о [политиках защиты приложений Microsoft Intune](what-is-app-protection-policy.md).

##  <a name="create-an-app-protection-policy"></a>Создание политики защиты приложений
1.  В рабочей нагрузке **Управление приложениями** выберите **Управление** > **Политики защиты приложений**.

2.  Откроется колонка **Политики защиты приложений**, в которой можно создавать и изменять политики. Выберите **Добавить политику**.

  ![Снимок экрана: колонка "Добавление политики"](../media/app-protection-add-policy.png)

3.  Введите имя для политики, добавьте краткое описание и выберите тип платформы, чтобы создать политику для iOS или Android. Для каждой платформы можно создать несколько политик.

4.  Щелкните **Приложения**, чтобы открыть колонку **Приложения**, где приводится список доступных приложений. Выберите в списке одно или несколько приложений, которые вы хотите сопоставить с создаваемой политикой. Выбрав приложения, нажмите кнопку **Выбрать** в нижней части колонки **Приложения**, чтобы сохранить выбранные элементы.

    > [!IMPORTANT]
    > Для создания политики необходимо выбрать хотя бы одно приложение.

5.  В колонке **Добавление политики** щелкните **Настроить обязательные параметры**, чтобы открыть колонку параметров политики.

    Существуют две категории параметров политики: **перемещение данных** и **доступ**.  Политики перемещения данных применяются к перемещению данных в приложение и из него, а политики доступа определяют, как конечный пользователь получает доступ к приложениям в рабочем контексте.
    Чтобы вы быстрее могли приступить к работе, параметры политики снабжены значениями по умолчанию. Если значения по умолчанию удовлетворяют вашим требованиям, никаких изменений вносить не нужно.

    > [!TIP]
    > Эти параметры политики применяются только при использовании приложения в рабочем контексте.  Когда конечный пользователь применяет приложение в личных целях, эти политики на него не распространяются.



6.  Нажмите кнопку **ОК**, чтобы сохранить конфигурацию. Выполняется возврат к колонке **Add a policy** (Добавить политику). Щелкните **Создать** для создания политики и сохранения параметров.


После завершения создания политики, описанного в предыдущей процедуре, политика не развертывается ни для одного из пользователей. Чтобы развернуть политику, см. следующий раздел "Развертывание политики для пользователей".

## <a name="deploy-a-policy-to-users"></a>Развертывание политики для пользователей

1.  В колонке **Политика** щелкните **Группы пользователей**, чтобы открыть колонку **Группы пользователей**. Выберите пункт **Добавить группу пользователей** в колонке **Группы пользователей**, чтобы открыть колонку **Добавить группу пользователей**.

  ![Снимок экрана: колонка "Группы пользователей" с выделенным пунктом меню "Добавить группу пользователей"](../media/app-protection-policy-add-users.png)

2.  В колонке **Add user group** (Добавить группу пользователей) отображается список групп пользователей. Этот список включает в себя все группы безопасности в вашем **Azure Active Directory**. Выберите группы пользователей, к которым должна применяться эта политика, а затем нажмите кнопку **Выбрать**. При нажатии кнопки **Выбрать** политика развертывается для пользователей.
  ![Снимок экрана: колонка "Добавление группы пользователей" со списком пользователей Azure Active Directory](../media/azure-ad-user-group-list.png)

Вы создали политику и развернули ее для пользователей.

Эта политика распространяется только на пользователей с назначенными лицензиями Microsoft Intune. Эта политика не распространятся на пользователей из выбранной вами группы безопасности, у которых нет назначенной лицензии Microsoft Intune.

>[!IMPORTANT]
> При использовании Intune с Configuration Manager для управления устройствами iOS и Android политика применяется только к пользователям, находящимся непосредственно в выбранной вами группе. Члены дочерних групп, вложенных в выбранную вами группу, не затрагиваются.

Конечные пользователи могут загрузить приложения из магазина App Store или Google Play. Дополнительные сведения см. на странице
* [Что происходит при управлении приложением Android с помощью политик защиты приложений](app-protection-enabled-android-apps.md)
* [Что происходит при управлении приложением iOS с помощью политик защиты приложений](app-protection-enabled-ios-apps.md)

##  <a name="change-existing-policies"></a>Изменение существующих политик
Вы можете изменить существующую политику и применить ее к целевым пользователям. Однако при изменении существующих политик пользователи, которые уже выполнили вход в приложения, не заметят никаких изменений в течение 8 часов.

Чтобы сразу увидеть эффект изменений, пользователям необходимо выйти из приложений и войти снова.

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>Изменение списка приложений, сопоставленных с политикой

1.  В колонке **Политика приложения** выберите политику, которую хотите изменить. Открывается колонка, соответствующая недавно выбранной политике.

2.  В колонке политики щелкните **Целевые приложения**, чтобы открыть список приложений.

3.  Удалите или добавьте приложения в списке и щелкните значок **Сохранить** для сохранения изменений.

### <a name="to-change-the-list-of-user-groups"></a>Изменение списка групп пользователей

1.  В колонке **Политика приложения** выберите политику, которую хотите изменить. Открывается колонка, соответствующая выбранной политике.

2.  В колонке политики щелкните **Группы пользователей**, чтобы открыть колонку **Группа пользователей**, в которой приводится список текущих групп пользователей с этой политикой.

3.  Чтобы добавить новую группу пользователей в политику, щелкните **Добавить группу пользователей** и выберите группу пользователей. Нажмите кнопку **Выбрать**, чтобы развернуть политику для выбранной группы.

4.  Чтобы удалить группу пользователей, выделите ее. Затем нажмите кнопку с многоточием (...) и кнопку **Удалить** для удаления группы.
  ![Снимок экрана: кнопка "Удалить"](../media/app-protection-policy-delete-user.png)

### <a name="to-change-policy-settings"></a>Изменение параметров политики

1.  В колонке **Политика приложения** выберите политику, которую хотите изменить. Открывается колонка, соответствующая недавно выбранной политике.


2.  Щелкните **Параметры политики**, чтобы открыть колонку **Параметры политики**.

3.  Измените параметры и щелкните значок **Сохранить** для сохранения изменений.

## <a name="policy-settings"></a>Параметры политики
Чтобы просмотреть полный список параметров политики для iOS и Android, выберите один из следующих элементов:

> [!div class="op_single_selector"]
- [Политики iOS](ios-app-protection-policy-settings.md)
- [Политики Android](android-app-protection-policy-settings.md)

## <a name="next-steps"></a>Дальнейшие действия
[Мониторинг соответствия требованиям и состояния пользователей](monitor-app-protection-policies-with-microsoft-intune.md)

### <a name="see-also"></a>См. также
* [Что происходит при управлении приложением Android с помощью политик защиты приложений](app-protection-enabled-android-apps.md)
* [Что происходит при управлении приложением iOS с помощью политик защиты приложений](app-protection-enabled-ios-apps.md)
