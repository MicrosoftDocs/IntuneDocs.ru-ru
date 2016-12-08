---
title: "Обеспечение регистрации устройств | Microsoft Intune"
description: "Задание центра MDM и обеспечение регистрации для устройств iOS, Windows, Android и Mac."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d3215e7-0a5c-44bd-afb0-aeafce98c43f
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 031cf995da4fa46b244b65a6b1c51b6a1aa00d9f
ms.openlocfilehash: 8c3076b26844669f9927478b5847f88f2265c6c9


---

# <a name="enroll-mobile-devices-and-install-an-app"></a>Регистрация мобильных устройств и установка приложения
Чтобы настроить управление мобильными устройствами с помощью Intune, необходимо сначала задать *центр управления мобильными устройствами*, который идентифицирует службу, позволяющую управлять устройствами, связанными с учетной записью. В этом руководстве предполагается, что вместо System Center Configuration Manager будет использоваться служба Intune. Задав центр управления мобильными устройствами, можно включить управление для платформ устройств и зарегистрировать устройства с помощью приложения корпоративного портала.

## <a name="enable-device-enrollment"></a>Обеспечение регистрации устройств

1. **Превращение Intune в центр управления мобильными устройствами.**
    В [консоли администрирования Intune](https://manage.microsoft.com/) щелкните **Администратор** > **Управление мобильными устройствами** и в разделе **Задачи** выберите **Set MDM Authority** (Задать центр управления мобильными устройствами).  

2. Выберите **Да** в диалоговом окне "Центр MDM" .

    ![Консоль администрирования. Настройка MDM в Intune](./media/mdmAuthority.png)

## <a name="choose-how-to-enroll-devices"></a>Выбор способа регистрации устройств

Intune может управлять устройствами различными способами в зависимости от требований вашей компании. "Принеси свое устройство" (BYOD), корпоративные устройства, "выбери свое устройство" (CYOD) и устройства в полноэкранном режиме — это лишь несколько доступных сценариев регистрации.

Выполните следующие действия, чтобы [выбрать способ регистрации мобильных устройств](choose-how-to-enroll-devices1.md).

## <a name="enable-mdm-for-your-device-platform"></a>Включение MDM для вашей платформы устройств
Регистрацию необходимо включить для устройств iOS, Mac и Android for Work, чтобы установить отношения между поставщиком платформы и клиентом Intune. Для устройств Windows и Android не требуются дополнительные действия, но можно упростить регистрацию устройств Windows для пользователей, создав специальную запись реестра DNS.

Включите регистрацию устройств для платформы устройств, которой необходимо управлять. В зависимости от используемой платформы есть различные требования:

-  [iOS и macOS](https://docs.microsoft.com/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune.md);
-  [компьютер с Windows](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune);
-  [Windows 10 Mobile и Windows Phone](https://docs.microsoft.com/intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune);
- [Android for Work](https://docs.microsoft.com/intune/deploy-use/set-up-android-for-work)

После включения регистрации пользователи могут скачать приложение корпоративного портала на устройство и завершить процесс регистрации устройства.

### <a name="enable-company-owned-device-enrollment"></a>Обеспечение регистрации устройств, принадлежащих компании
Вы также можете реализовать различные сценарии [регистрации устройств, принадлежащих компании](https://docs.microsoft.com/intune/deploy-use/manage-corporate-owned-devices), включая следующие:
- [программа регистрации устройств Apple](https://docs.microsoft.com/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune);
- [помощник по настройке регистрации Apple Configurator](https://docs.microsoft.com/intune/deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune);
- [помощник по настройке регистрации Apple Configurator](https://docs.microsoft.com/intune/deploy-use/ios-direct-enrollment-in-microsoft-intune);
- [диспетчер регистрации устройств](https://docs.microsoft.com/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).

### <a name="next-steps"></a>Дальнейшие действия
Поздравляем! Вы завершили последний шаг *краткого руководства по Intune*. Теперь, когда начальная настройка завершена, рассмотрите возможность включения дополнительных функций MDM.

>[!div class="step-by-step"]

>[&larr; **Регистрация устройств**](.\start-with-a-paid-subscription-to-microsoft-intune-step-8.md)     [**Задачи, выполняемые после настройки** &rarr;](.\post-configuration-tasks.md)  



<!--HONumber=Dec16_HO1-->

