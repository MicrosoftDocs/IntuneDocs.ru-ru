---
title: "Соединитель MTD Zimperium в Intune"
titleSuffix: Intune on Azure
description: "Интеграция соединителя Zimperium с Intune"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 09/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 975d8d84-792a-41ad-925a-4a7f1ae4dcaf
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 78214293a66784d4bc05e441c2c1cdbf718b0a9a
ms.sourcegitcommit: d434dfab7ef7a6c4082d675717fa22d5581b4f51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2017
---
# <a name="zimperium-mobile-threat-defense-connector-with-intune"></a>Соединитель Mobile Threat Defense Zimperium с Intune

Вы можете управлять доступом к корпоративным ресурсам с мобильных устройств посредством условного доступа на основании оценки рисков, проведенной Zimperium, — решением для защиты от угроз на мобильных устройствах, интегрированным с Microsoft Intune. Оценка рисков основана на данных телеметрии, собранных с устройств, на которых выполняется приложение Zimperium.

Вы можете настроить политики условного доступа на основе оценки рисков Zimperium, реализуемой с помощью политик соответствия устройств Intune. Эти политики также можно использовать для разрешения или запрета доступа несоответствующих устройств к корпоративным ресурсам на основании обнаруженных угроз.

## <a name="how-do-intune-and-zimperium-help-protect-your-company-resources"></a>Как Intune и Zimperium помогают защитить ресурсы вашей организации?

Мобильное приложение Zimperium для Android или iOS регистрирует сведения о файловой системе и сетевом стеке, а также данные телеметрии устройств и приложений (при наличии) и отправляет их в облачную службу Zimperium для вычисления риска в отношении угроз для мобильного устройства.

Политика соответствия устройств Intune включает правило для защиты мобильных устройств от угроз Zimperium, основанное на оценке рисков Zimperium. При включении этого правила Intune оценивает соответствие устройства заданной политике. Если устройство определяется как несоответствующее, его доступ к таким ресурсам, как Exchange Online и SharePoint Online, блокируется. Пользователи заблокированных устройств получают от мобильного приложения Zimperium рекомендации по устранению проблемы и восстановлению доступа к корпоративным ресурсам.

## <a name="sample-scenarios"></a>Примеры сценариев

Ниже приведены некоторые сценарии интеграции Zimperium с Intune.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Управление доступом на основании оценки угроз от вредоносных приложений

При обнаружении на устройствах вредоносного ПО можно заблокировать до устранения угрозы следующие функции.

-   Подключение к корпоративной электронной почте

-   Синхронизация корпоративных файлов с помощью приложения OneDrive для работы

-   Доступ к приложениям организации

**Блокировка при обнаружении вредоносных программ:**

![Обнаружены вредоносные приложения](./media/Maliciousapps_blocked_Zimperium.png)

**Доступ предоставлен после устранения угрозы:**

![Обнаружены вредоносные приложения, доступ предоставлен](./media/maliciousapps_unblocked_Zimperium.png)

### <a name="control-access-based-on-threat-to-network"></a>Управление доступом на основании оценки угрозы для сети

Обнаружение угроз типа **злоумышленник в середине** и защита доступа к сетям Wi-Fi на основе рисков для устройств.

**Блокировка доступа к сети через Wi-Fi:**

![Блокировка доступа к сети через Wi-Fi](./media/network_wifi_blocked_Zimperium.png)

**Доступ предоставлен после устранения угрозы:**

![Доступ предоставляется после устранения угрозы](./media/network_wifi_unblocked_Zimperium.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Управление доступом к SharePoint Online на основании оценки угрозы для сети

Обнаружение угроз типа **злоумышленник в середине** и предотвращение синхронизации корпоративных файлов на основе риска для устройств.

**Блокирование SharePoint Online при обнаружении сетевых угроз:**

![Блокировка SharePoint Online при обнаружении сетевых угроз](./media/network_spo_blocked_Zimperium.png)

**Доступ предоставлен после устранения угрозы:**

![Пример предоставления доступа к Sharepoint после устранения угрозы](./media/network_spo_unblocked_Zimperium.png)

## <a name="supported-platforms"></a>Поддерживаемые платформы

-   **Android 4.1 и более поздней версии**.

-   **iOS 8 и более поздние версии**

## <a name="prerequisites"></a>Необходимые компоненты

-   Azure Active Directory Premium

-   Подписка Microsoft Intune

-   Подписка на службу Mobile Threat Defense Zimperium

    -   Дополнительные сведения см. на [веб-сайте Zimperium](https://www.zimperium.com/zips-mobile-ips).

## <a name="next-steps"></a>Дальнейшие действия

- [Интеграция Zimperium с Intune](zimperium-mtd-connector-integration.md)

- [Настройка приложений Zimperium](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Создание политики соответствия устройств Zimperium](mtd-device-compliance-policy-create.md)

- [Включение соединителя MTD Zimperium](mtd-connector-enable.md)