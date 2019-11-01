---
title: Включение защищенного режима iOS в Microsoft Intune
titleSuffix: ''
description: Узнайте, как включить защищенный режим iOS в Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/15/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 8190814-07f0-42d8-9b3a-87c67dd2b7ed
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 99f27992009332a2a5fae0768225d8c69d3ac5ad
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509412"
---
# <a name="turn-on-ios-supervised-mode"></a>Включение защищенного режима iOS


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Защищенный режим Apple iOS дает администраторам дополнительные возможности управления устройствами Apple при масштабном развертывании корпоративных устройств. Например, можно ограничить использование AirDrop или запретить пользователям менять имена устройств. Список параметров, требующих защищенного режима, см. в статье [Параметры ограничений для устройств iOS в Microsoft Intune](../configuration/device-restrictions-ios.md).

Intune поддерживает защищенный режим в рамках [Программы регистрации устройств Apple (DEP)](../enrollment/device-enrollment-program-enroll-ios.md).

Список средств управления Apple, требующих защиты, см. в статье [Payload settings reference](http://help.apple.com/configurator/mac/2.4/#/cad5370d089) (Справочник по параметрам полезной нагрузки) на сайте Apple.

## <a name="turn-on-supervised-mode-during-enrollment"></a>Включение защищенного режима во время регистрации

В Intune защищенный режим для устройств можно включить при [создании профиля регистрации Apple в DEP](../enrollment/device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile). В разделе **Параметры управления устройствами** установите флажок **Защищено**.

## <a name="turn-on-supervised-mode-after-enrollment"></a>Включение защищенного режима после регистрации

После регистрации единственный способ включить защищенный режим — подключить устройство iOS к компьютеру Mac и воспользоваться [Apple Configurator](../enrollment/apple-configurator-enroll-ios.md) (при этом устройство будет сброшено). После регистрации настроить для устройства защищенный режим в Intune невозможно.

## <a name="identify-a-supervised-device"></a>Определение защищенного устройства

Определить, защищено ли устройство, можно на экране блокировки или на странице **Об этом устройстве**.
- На экране блокировки устройства должно быть сообщение **Этим iPhone управляет "Название организации"** .
- На странице **Об этом устройстве** должно быть сообщение **Это устройство iPhone защищено. "Название организации" может отслеживать ваш интернет-трафик и обнаруживать устройство**.

## <a name="next-steps"></a>Дальнейшие шаги

Сведения о других вариантах управления устройствами см. в статье [Что такое управление устройствами с помощью Microsoft Intune](device-management.md).