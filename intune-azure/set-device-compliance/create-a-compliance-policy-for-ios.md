---
title: "Создание политики соответствия для iOS"
titleSuffix: Intune Azure preview
description: "Предварительная версия Intune Azure. Узнайте, как создать политику соответствия требованиям для устройств iOS."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: c2ace3061e175a6eefd864bdda176651cc09a5b1
ms.lasthandoff: 02/18/2017


---

# <a name="how-to-create-a-device-compliance-policy-for-ios-devices-in-intune-azure-preview"></a>Создание политики соответствия требованиям для устройств iOS в предварительной версии Intune Azure


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Политики соответствия требованиям создаются для каждой платформы.  Их можно создать на портале Azure. Дополнительные сведения о политике соответствия требованиям для устройства см. в [этой статье](what-is-device-compliance.md). Сведения о предварительных требованиях, которые необходимо выполнить при создании политики соответствия требованиям, см. в статье [Общие сведения о соответствии устройств политике в предварительной версии Intune Azure](get-started-with-device-compliance.md).

В таблице ниже описано управление несоответствующими параметрами при использовании политики соответствия требованиям с политикой условного доступа.

-------------------------------


| **Параметр политики** | **Устройства iOS 8.0 и более поздних версий** |
| --- | --- |
| **Конфигурация ПИН-кода или пароля** | Исправлено |   
| **Шифрование устройства** | Исправлено (путем установки ПИН-кода) |
| **Устройство со снятой защитой или административным доступом** | Карантин (не параметр)
| **Профиль электронной почты** | Помещено в карантин |
|**Минимальная версия ОС** | Помещено в карантин |
| **Максимальная версия ОС** | Помещено в карантин |  
| **Аттестация работоспособности Windows** | Неприменимо |  
----------------------------


**Исправлено** = операционная система устройства обеспечивает соответствие. (Например, пользователь вынужден установить ПИН-код.)

**Карантин** = операционная система устройства не обеспечивает соответствие. (Например, устройства Android не требуют от пользователя шифрования устройства.) Если устройство не соответствует требованиям, выполняются указанные далее действия.

- Устройство блокируется, если к пользователю применяется политика условного доступа.
- Корпоративный портал будет уведомлять пользователя обо всех проблемах соответствия.

## <a name="create-a-compliance-policy-in-the-azure-portal"></a>Создание политики соответствия требованиям на портале Azure

1. В колонке **Intune** выберите **Задание соответствия устройства требованиям**. В разделе **Управление** выберите **Все политики соответствия устройства** и щелкните **Создать**.
2. Введите имя, описание и выберите платформу, к которой должна применяться данная политика.
3. Выберите **Требования соответствия**, чтобы указать значения параметров **Безопасность**, **Работоспособность устройства** и **Свойства устройства**. По завершении нажмите кнопку **ОК**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** blade, choose **Add** to create a new action.  The action parameters blade allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
7. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="assign-user-groups"></a>Назначение групп пользователей

Чтобы назначить пользователям политику соответствия требованиям, выберите настроенную политику. Имеющиеся политики можно найти в колонке **Compliance –policies** (Политики соответствия).

1. Выберите политику, которую необходимо назначить пользователям, и щелкните **Назначения**. Откроется колонка, где можно выбрать **группы безопасности Azure Active Directory** и назначать их политике.
2. Щелкните **Выбрать группы**, чтобы открыть колонку, в которой отображаются группы безопасности Azure AD.  При нажатии кнопки **Выбрать** политика развертывается для пользователей.

Политика применена к пользователям.  Устройства пользователей, на которые распространяется политика, будут проверяться на соответствие требованиям.

<!---## Compliance policy settings--->

## <a name="system-security-settings"></a>Параметры безопасности системы

### <a name="password"></a>Пароль

- **Требовать ввода пароля для разблокировки мобильных устройств.** Задайте значение **Да** для запроса пароля при доступе к устройству. Устройства iOS, использующие пароли, шифруются.
- **Разрешить простые пароли.** Задайте значение **Да**, чтобы пользователи могли создавать простые пароли, например **1234** или **1111**.
- **Минимальная длина пароля.** Указывает минимальное число цифр или символов в пароле.
- **Требуемый тип пароля.** Указывает, какой пароль должны создавать пользователи — **буквенно-цифровой** или **цифровой**.
- **Минимальное число наборов символов.** Если для параметра **Требуемый тип пароля** задано значение **Буквенно-цифровой**, то этот параметр указывает минимальное число наборов символов, которое должен содержать пароль. Используются следующие четыре набора символов.
  - Строчные буквы
  - Прописные буквы
  - Символы
  - Числа

Чем больше значение, тем более сложный пароль нужно будет придумать пользователю.

Для устройств с iOS этот параметр определяет количество специальных символов (например, **!** , **#**, **&amp;**), которые нужно добавить в пароль.

- **Время бездействия (в минутах), по истечении которого требуется ввод пароля.** Укажите время бездействия, по истечении которого пользователю потребуется ввести пароль повторно.
- **Срок действия пароля (в днях).** Укажите число дней, по истечении которых пользователю понадобится создать пароль.
- **Вести журнал паролей.** Используйте этот параметр с параметром **Запретить использование предыдущих паролей**, чтобы запретить пользователям создавать пароли, совпадающие с прежними паролями.
- **Запретить использование предыдущих паролей.** Если выбран параметр **Вести журнал паролей**, укажите число ранее использованных паролей, которые нельзя использовать повторно.
- **Запрашивать пароль при выходе устройства из состояния простоя.** Используйте этот параметр вместе с параметром **Время бездействия (в минутах), по истечении которого требуется ввод пароля**. Пользователю будет предложено ввести пароль для доступа к устройству, если оно оставалось неактивным в течение времени, указанного в параметре **Время бездействия (в минутах), по истечении которого требуется ввод пароля**.

### <a name="email-profile"></a>Email profile (Профиль электронной почты)

- **Учетная запись почты должна управляться Intune.** Если для этого параметра задано значение **Да**, устройство должно использовать профиль электронной почты, развернутый на нем. Устройство считается несоответствующим в указанных далее ситуациях.
  - Профиль электронной почты развертывается в группе пользователей, отличной от группы пользователей, на которую ориентирована политика соответствия.
  - Пользователь уже настроил учетную запись электронной почты на устройстве, соответствующем профилю электронной почты Intune, развернутому на устройстве. Intune не может перезаписывать профиль, созданный пользователем, поэтому не может управлять им. Чтобы обеспечить соответствие требованиям, пользователь должен удалить существующие параметры электронной почты. После этого Intune сможет установить управляемый профиль электронной почты.
- **Select the email profile that must be managed by Intune** (Выберите профиль электронной почты, которым должен управлять Intune). Если выбран параметр **Учетная запись почты должна управляться Intune**, нажмите кнопку **Выбрать**, чтобы выбрать профиль электронной почты Intune. На устройстве должен быть профиль электронной почты.

Дополнительные сведения о профилях электронной почты см. в статье [Настройка доступа к корпоративной электронной почте с помощью профилей электронной почты с Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune).

## <a name="device-health-settings"></a>Параметры работоспособности устройства

- **На устройстве не должно быть снято ограничение на доступ к файловой системе или к корневому каталогу.** Если этот параметр включен, то устройства со снятой защитой будут считаться не соответствующими требованиям.

## <a name="device-properties"></a>Свойства устройства

- **Minimum OS required** (Минимальная требуемая ОС). Если устройство не соответствует требованию к минимальной версии ОС, оно будет отмечено как не соответствующее требованиям. Приводится ссылка на сведения о том, как выполнить обновление. По желанию пользователь может обновить свои устройства. После этого он сможет получить доступ к ресурсам компании.
- **Maximum OS version allowed** (Максимально допустимая версия ОС). Если устройство использует версию ОС, более позднюю по сравнению с указанной в правиле, доступ к ресурсам компании блокируется и пользователя просят связаться с ИТ-администратором. До изменения правила для разрешения конкретной версии ОС это устройство невозможно будет использовать для доступа к ресурсам компании.

<!--- ## Next steps

[How to monitor device compliance](monitor-device-compliance.md)--->
