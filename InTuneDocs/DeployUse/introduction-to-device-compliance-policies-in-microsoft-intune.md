---
# required metadata

title: Политики соответствия устройств | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 0775107a-6662-41c8-9404-be14bbb599f3

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Политики соответствия устройств в Microsoft Intune
## Что такое политика соответствия?
Чтобы защитить данные компании, необходимо убедиться в том, что устройства, используемые для доступа к данным и приложениям компании, соответствуют определенным правилам (например, использование ПИН-код для доступа к устройству и шифрование данных, хранящихся на устройстве). Набор таких правил называется политикой соответствия.

## Как использовать политики соответствия?
Политики соответствия можно использовать с политиками условного доступа для предоставления доступа только тем устройствам, которые отвечают правилам политики соответствия. Прочтите статью [Restrict access to email and O365 services (Ограничение доступа к электронной почте и службам Office 365)](restrict-access-to-email-and-o365-services-with-microsoft-intune.md), чтобы понять, как использовать две политики вместе.

Кроме того, политики соответствия можно использовать независимо от условного доступа. При независимом использовании происходит оценка целевых устройств и вывод сведений о них с указанием состояния соответствия. Например, может потребоваться сообщить от количестве незашифрованных устройств или количестве устройств со снятой защитой или административным доступом. Однако при независимом использовании отсутствуют ограничения на доступа к ресурсам компании.

Политики соответствия развертываются для пользователей. При развертывании политики соответствия для пользователя его устройства проверяются на соответствие.

В следующей таблице перечислены типы устройств, поддерживаемые политиками соответствия, а также способы управления несоответствующими параметрами при использовании политики с политикой условного доступа.

--------------

|Параметр политики| Windows 8.1 и более поздние версии| Windows Phone 8.1 и более поздней версии| iOS 6.0 и более поздних версий|Android 4.0 и более поздней версии<br/>Samsung KNOX Standard 4.0 и более поздние версии|
|-----|----|----|----|
|**Конфигурация ПИН-кода или пароля** |Исправлено|Исправлено|Исправлено|Помещено в карантин|
|**Шифрование устройства**|Н/Д|Исправлено|Исправлено (путем установки ПИН-кода)|Помещено в карантин|
|**Устройство со снятой защитой или административным доступом**|Н/Д|Н/Д|Карантин (не параметр)|Карантин (не параметр)|
|**Профиль электронной почты**|Н/Д|Н/Д|Помещено в карантин|Н/Д|
|**Минимальная версия ОС**|Помещено в карантин|Помещено в карантин|Помещено в карантин|Помещено в карантин|
|**Максимальная версия ОС**|Помещено в карантин| Помещено в карантин| Помещено в карантин| Помещено в карантин|
|**Аттестация работоспособности Windows**|Windows 10 и Windows 10 Mobile помещаются в карантин.<br /><br />Параметр не применим к Windows 8.1.|Н/Д|Н/Д|Н/Д|
--------------
**Исправлено**: соответствие обеспечивается операционной системой устройства (например, пользователь вынужден установить ПИН-код).  Параметр ни в коем случае не может быть несоответствующим.

**Карантин**: операционная система устройства не применяет шаги по обеспечению соответствия (например, не используется принудительное шифрование устройств Android пользователями). Если устройство не соответствует требованиям, выполняются указанные далее действия.

-   Устройство будет заблокировано, если пользователь является целью для политики условного доступа.

-   Корпоративный портал будет уведомлять пользователя о любых проблемах соответствия.

## Дальнейшие действия
[Создание политики соответствия устройства](create-a-device-compliance-policy-in-microsoft-intune.md)

[Развертывание и мониторинг политики соответствия устройства](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md)

### См. также
[Ограничение доступа к электронной почте и службам Office 365](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)


<!--HONumber=May16_HO2-->

