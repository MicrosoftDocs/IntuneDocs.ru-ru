---
title: Сброс секретных кодов для устройств с помощью Microsoft Intune в Azure | Документация Майкрософт
description: Удалите или сбросьте секретный код, используя соответствующее действие на устройствах, управляемых и наблюдаемых с помощью Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d7ca53786d372f53d63388fef1179ca271fdb9d9
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508588"
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>Сброс или удаление секретного кода устройства с помощью Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

В этом документе рассматривается как сброс секретного кода на уровне устройства, так и сброс секретного кода рабочего профиля на устройствах Android для бизнеса (ранее называвшихся устройствами Android for Work или AfW). Важно понимать различия между этими процедурами, так как к ним предъявляются разные требования. При сбросе секретного кода на уровне устройства он сбрасывается для всего устройства. При сбросе секретного кода рабочего профиля он сбрасывается только для рабочего профиля пользователя на корпоративном устройстве Android.

## <a name="supported-platforms-for-device-level-passcode-reset"></a>Поддерживаемые платформы для сброса секретного кода на уровне устройства

| Платформа | Поддержка |
| ---- | ---- |
| Устройства с Android 6.x или более ранними версиями | Да |
| Корпоративные устройства с Android в режиме терминала | Да |
| Устройства iOS | Да |
| Устройства iOS, зарегистрированные с помощью процедуры регистрации пользователей | Нет |
| Устройства с Android, зарегистрированные с помощью рабочего профиля | Нет |
| Устройства с Android 7.0 или более поздней версией | Нет |
| macOS | Нет |
| Windows | Нет |

Для устройств с Android это означает, что сброс секретного кода на уровне устройства поддерживается только на устройствах с Android 6.x или более ранними версиями либо на устройствах с Android для бизнеса, работающих в режиме киоска. Это связано с тем, что компания Google убрала возможность сброса секретного кода или пароля устройства с Android 7 из приложения с правами администратора устройства. Это относится ко всем поставщикам MDM.

## <a name="supported-platforms-for-android-enterprise-work-profile-passcode-reset"></a>Поддерживаемые платформы для сброса секретного кода рабочего профиля на корпоративном устройстве с Android

| Платформа | Поддержка |
| ---- | ---- |
| Корпоративные устройства с Android 8.0 или более поздней версией, зарегистрированные с помощью рабочего профиля | Да |
| Корпоративные устройства с Android 7.x или более ранней версией, зарегистрированные с помощью рабочего профиля | Нет |
| Устройства с Android 7.x или более ранней версией | Нет |

Чтобы создать секретный код рабочего профиля, используйте действие "Сбросить секретный код". Это действие запрашивает сброс секретного кода и создает новый временный секретный код только для рабочего профиля. 

## <a name="reset-a-passcode"></a>Сброс секретного кода


1. Войдите на [портал Azure](https://portal.azure.com) с любой из следующих ролей: глобальный администратор Azure Active Directory, администратор службы Intune в Azure Active Directory, оператор справочной службы или администратор ролей.
2. Выберите **Все службы**, отфильтруйте список по **Intune** и выберите **Microsoft Intune**.
3. Выберите **Устройства**, а затем — **Все устройства**.
4. Выберите нужное устройство в списке управляемых устройств и щелкните **Дополнительно**. Затем выберите удаленное действие **Удалить секретный код**.

## <a name="reset-android-work-profile-passcodes"></a>Сброс секретных кодов рабочих профилей Android

Конечные пользователи поддерживаемых корпоративных устройств Android, зарегистрированных с помощью рабочих профилей, получают новый пароль для разблокировки управляемого профиля или запрос защиты управляемого профиля.

Конечные пользователи корпоративных устройств Android 8.x или более поздней версии, зарегистрированных с помощью рабочих профилей, получают уведомление о необходимости активировать сброс секретного кода сразу после завершения регистрации. Уведомление отображается в том случае, если требуется и задан пароль рабочего профиля. После ввода секретного кода уведомление закрывается.


## <a name="remove-ios-passcodes"></a>Удаление секретных кодов iOS

На устройствах iOS секретные коды не сбрасываются, а удаляются. Если задана политика соответствия требованиям для секретного кода, устройство предлагает пользователю указать новый секретный код в разделе параметров.

## <a name="next-steps"></a>Дальнейшие шаги

Чтобы просмотреть состояние выполненного действия, на панели **Устройства** выберите **Действия устройства**.