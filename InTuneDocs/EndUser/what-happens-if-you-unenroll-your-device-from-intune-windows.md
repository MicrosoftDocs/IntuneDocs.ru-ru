---
# required metadata

title: Что происходит при отмене регистрации устройства в Intune? | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 47e03edb-0c57-4e25-8e89-4a1069267b8c

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Что происходит при отмене регистрации устройства в Intune?

При удалении приложения корпоративного портала с устройства отменяется регистрация этого устройства в Intune. Для получения дополнительных сведений выберите ссылку, соответствующую типу устройства.

- [Windows 10 Mobile, Windows 8.1, Windows 8, Windows 7, Vista](#windows-10-mobile--8-1,-windows-8,-windows-7,-vista)
- [Windows 10, Windows 8.1 или Windows Phone 8](#windows-10--windows-8-1-or-windows-phone-8)
- [Windows RT с Windows 8.1 или Windows RT](#windows-rt-running-windows-8-1-or-windows-rt)


## Windows 10, Windows 8.1, Windows 8, Windows 7, Vista

-   Устройство больше не будет отображаться на корпоративном портале, и вы не сможете устанавливать приложения с корпоративного портала.

-   Если вы установили клиентское программное обеспечение Intune, оно будет удалено с компьютера.

-   Программное обеспечение Intune Endpoint Protection удаляется с компьютера. Если на компьютере установлено другое ПО для защиты от вирусов и оно отключено, это приложение можно будет снова включить после удаления Intune Endpoint Protection. Проверьте компьютер после удаления на корпоративном портале.

    > Если другое ПО для защиты от вирусов не включено повторно или не установлено, ваш компьютер может оказаться уязвим для вирусов и вредоносного ПО.

-   Параметры, измененные на устройстве после его добавления, например выключение камеры, перестанут действовать.

-   Компьютер больше не будет получать автоматические обновления ПО и антивирусной программы через службу Intune. При этом в зависимости от настроек компьютер может продолжать получать обновления с помощью служб Windows Server Update Services, Центра обновления Windows или Центра обновления Майкрософт.

Дополнение для Windows 8.1:

-   вы больше не сможете использовать корпоративные приложения и данные на устройстве;

-   некоторые почтовые приложения, например Почта Windows, потеряют доступ к корпоративной почте, хранящейся на устройстве;

-   вы можете потерять возможность подключения к корпоративной сети по Wi-Fi и VPN;

-   вы можете потерять доступ к ряду корпоративных ресурсов, например файловым ресурсам или внутренним веб-сайтам, с вашего устройства;

## Windows 10 Mobile, Windows Phone 8.1 или Windows Phone 8

-   Приложение корпоративного портала удаляется с устройства, поэтому устройство больше не будет отображаться на корпоративном портале и вы не сможете устанавливать приложения из приложения или с веб-сайта корпоративного портала.

-   вы больше не сможете использовать корпоративные приложения и данные на устройстве;

-   параметры, измененные на устройстве после его добавления, например выключение камеры или включение требований к паролю, перестанут действовать;

    > [!IMPORTANT]
    > Единственное исключение — политики шифрования, которые продолжат работать. Если политика компании требует использовать шифрование в Windows Phone, то единственный способ расшифровки — сброс настроек телефона в меню **Настройки** Windows Phone.

## Windows RT с Windows 8.1 или Windows RT

-   Приложение корпоративного портала удаляется с устройства, поэтому устройство больше не будет отображаться на корпоративном портале и вы не сможете устанавливать приложения с корпоративного портала.

-   вы больше не сможете использовать корпоративные приложения и данные на устройстве;

-   параметры, измененные на устройстве после его добавления, например выключение камеры или включение требований к паролю, перестанут действовать;

-   вы можете потерять возможность подключения к корпоративной сети по Wi-Fi и VPN;

-   вы можете потерять доступ к ряду корпоративных ресурсов, например файловым ресурсам или внутренним веб-сайтам, с вашего устройства;

-   некоторые почтовые приложения, например Почта Windows, потеряют доступ к корпоративной почте, хранящейся на устройстве;

При удалении устройства Windows RT происходит следующее:

-   Приложение корпоративного портала удаляется с устройства, поэтому устройство больше не будет отображаться на корпоративном портале и вы не сможете устанавливать приложения с корпоративного портала.

-   вы больше не сможете использовать корпоративные приложения и данные на устройстве;

-   параметры, измененные на устройстве после его добавления, например выключение камеры или включение требований к паролю, перестанут действовать;


### См. также
[Использование устройства Windows в Intune](using-your-windows-device-with-intune.md)

<!--HONumber=May16_HO2-->

