---
title: Регистрация устройств с рабочим профилем Android для бизнеса в Intune
titleSuffix: Microsoft Intune
description: Узнайте, как регистрировать устройства с рабочим профилем Android для бизнеса в Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 5/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4339f98ed133c3426faee8bd4b18024fd2648606
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503353"
---
# <a name="set-up-enrollment-of-android-enterprise-work-profile-devices"></a>Настройка регистрации устройств с рабочим профилем Android для бизнеса

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune помогает разделить рабочие и личные данные при развертывании приложений и параметров на устройствах с рабочим профилем Android для бизнеса. Дополнительные сведения об Android для бизнеса см. в разделе [Требования Android для бизнеса](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

Чтобы настроить управление рабочими профилями Android для бизнеса, сделайте следующее:

1. [Подключите учетную запись клиента Intune к учетной записи Android для бизнеса](connect-intune-android-enterprise.md).
2. Укажите параметры регистрации рабочего профиля Android для бизнеса. Рабочие профили Android для бизнеса [поддерживаются только на некоторых устройствах Android](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012%20style=%22target=new_window%22). Любое устройство, которое поддерживает рабочие профили Android для бизнеса, также поддерживает управление администратором устройства Android. Intune позволяет указать, как следует управлять устройствами, которые поддерживают рабочие профили Android для бизнеса, в разделе [Ограничения регистрации](enrollment-restrictions-set.md).
    - **Блокировать**:  Все устройства Android, включая устройства, поддерживающие рабочие профили Android для бизнеса, будут зарегистрированы как устройства администратора устройств Android, кроме случаев, когда регистрация администратора устройства Android также заблокирована. 
    - **Разрешить (по умолчанию)** : все устройства, поддерживающие рабочие профили Android для бизнеса, регистрируются в качестве устройств с рабочим профилем Android. Любое устройство Android, которое не поддерживает рабочие профили Android для бизнеса, регистрируется как устройство администратора устройства Android, кроме случаев, когда регистрация администратора устройства Android также заблокирована. 
> [!NOTE]
> Значение по умолчанию **Allow** (Разрешить) — действительно для новых клиентов по состоянию на июль 2019. Изменения ограничений регистрации не затронут всех предыдущих клиентов, они будут видеть, какие политики установлены ими в ограничениях регистрации. Для предыдущих клиентов, которые никогда не изменяли ограничения регистрации, по умолчанию для рабочих профилей Android для бизнеса по-прежнему будет использоваться **Блок**.

3. [Расскажите пользователям, как регистрировать устройства](/intune-user-help/create-a-work-profile-and-enroll-your-device-in-intune-android).  

Если необходимо зарегистрировать устройства с использованием рабочих профилей Android для бизнеса, но эти устройства уже были зарегистрированы администратором устройства Android, для таких устройств сначала следует отменить регистрацию, а затем повторно зарегистрироваться.
> [!NOTE]
> Администратор может сделать это удаленно, используя функцию **Прекратить использование**. Эту функцию можно найти в меню "Действия" после выбора устройства из колонки **Все устройства**.

При регистрации устройств с рабочим профилем Android для бизнеса с использованием учетной записи [диспетчера регистрации устройств](device-enrollment-manager-enroll.md) на одну такую запись можно зарегистрировать не более 10 устройств.

Дополнительные сведения см. в статье [Данные, отправляемые Intune в Google](../protect/data-intune-sends-to-google.md).

## <a name="next-steps-for-android-enterprise-work-profiles"></a>Дальнейшие шаги по использованию рабочих профилей Android для бизнеса
- [Назначение приложений управляемого Google Play для корпоративных устройств с Android с помощью Intune](../apps/apps-add-android-for-work.md)
- [Применение параметров функций на устройствах с помощью профилей устройств в Microsoft Intune](../configuration/device-profiles.md)

## <a name="see-also"></a>См. также

[Настройка устройств Android для бизнеса и устранение неполадок с ними в Microsoft Intune](https://support.microsoft.com/help/4476974)