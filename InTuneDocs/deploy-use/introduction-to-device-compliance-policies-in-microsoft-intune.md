---
title: "Политики соответствия устройств | Microsoft Intune"
description: "В этом разделе описаны политики соответствия устройства и то, как они действуют."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0775107a-6662-41c8-9404-be14bbb599f3
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: b41307f620284315e4c71b0d0292b229753876ad


---

# <a name="device-compliance-policies-in-microsoft-intune"></a>Политики соответствия устройств в Microsoft Intune
## <a name="what-is-a-compliance-policy"></a>Что такое политика соответствия?
Для защиты корпоративных данных необходимо проследить за тем, чтобы устройства, используемые для доступа к корпоративным приложениям и данным, соответствовали определенным правилам. Эти правила могут включать использование ПИН-кода для доступа к устройствам и шифрование данных, хранящихся на устройствах. Набор таких правил называется политикой соответствия.

## <a name="how-should-i-use-compliance-policies"></a>Как использовать политики соответствия?
Политики соответствия требованиям можно использовать совместно с политиками условного доступа для предоставления доступа к электронной почте и другим службам только тем устройствам, которые отвечают правилам политики соответствия. Дополнительные сведения об одновременном использовании двух политик см. в статье [Ограничение доступа к электронной почте и службам Office 365](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).

Кроме того, политики соответствия можно использовать независимо от условного доступа. При независимом использовании политики соответствия происходит оценка целевых устройств и вывод сведений о них с указанием состояния соответствия. Например, может потребоваться сообщить от количестве незашифрованных устройств или количестве устройств со снятой защитой или административным доступом. Однако если политики соответствия используются независимо друг от друга, доступ к корпоративным ресурсам не ограничивается.

Политики соответствия развертываются для пользователей. При развертывании политики соответствия для пользователя его устройства проверяются на соответствие.
Дополнительные сведения о том, сколько времени требуется мобильным устройствам для получения политики после развертывания, см. в разделе [Управление настройками и функциями на устройствах](https://docs.microsoft.com/en-us/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies#frequently-asked-questions-about-intune-policies)

Ниже перечислены типы устройств, которые поддерживает политика соответствия. В таблице также описано управление несоответствующими параметрами при использовании политики соответствия с политикой условного доступа.

-----------------------------

|Параметр политики| Windows 8.1 и более поздние версии| Windows Phone 8.1 и более поздней версии| Устройства iOS 8.0 и более поздней версии|Android 4.0 и более поздней версии<br/>Samsung KNOX Standard 4.0 и более поздние версии|
|-----|----|----|----|----|
|**Конфигурация ПИН-кода или пароля** |Исправлено|Исправлено|Исправлено|Помещено в карантин|
|**Шифрование устройства**|Неприменимо|Исправлено|Исправлено (путем установки ПИН-кода)|Помещено в карантин|
|**Устройство со снятой защитой или административным доступом**|Неприменимо|Неприменимо|Карантин (не параметр)|Карантин (не параметр)|
|**Профиль электронной почты**|Неприменимо|Неприменимо|Помещено в карантин|Неприменимо|
|**Минимальная версия ОС**|Помещено в карантин|Помещено в карантин|Помещено в карантин|Помещено в карантин|
|**Максимальная версия ОС**|Помещено в карантин|Помещено в карантин|Помещено в карантин|Помещено в карантин|
|**Аттестация работоспособности Windows**|Windows 10 и Windows 10 Mobile помещаются в карантин.<br /><br />Неприменимо: Windows 8.1|Неприменимо|Неприменимо|Неприменимо|

------------------------------

**Исправлено** = операционная система устройства обеспечивает соответствие. (Например, пользователь вынужден установить ПИН-код.)

**Карантин** = операционная система устройства не обеспечивает соответствие. (Например, устройства Android не требуют от пользователя шифрования устройства.) Если устройство не соответствует требованиям, выполняются указанные далее действия.

-   Устройство блокируется, если к пользователю применяется политика условного доступа.

-   Корпоративный портал будет уведомлять пользователя обо всех проблемах соответствия.

## <a name="next-steps"></a>Дальнейшие действия
[Создание политики соответствия устройства](create-a-device-compliance-policy-in-microsoft-intune.md)

[Развертывание и мониторинг политики соответствия устройства](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md)

### <a name="see-also"></a>См. также
[Ограничение доступа к электронной почте и службам Office 365](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->

