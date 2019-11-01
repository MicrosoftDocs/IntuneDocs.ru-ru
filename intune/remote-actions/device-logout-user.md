---
title: Выход из системы для пользователя устройства iOS
titleSuffix: Microsoft Intune
description: Вы можете узнать, как выполнить выход из системы для пользователя устройства iOS с помощью Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/27/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 702bc46c-1a6f-4689-bd53-3b778a447baa
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8336f5b29cd21bb6875285177071542080eb95f3
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509460"
---
# <a name="logout-the-current-user-on-intune-managed-ios-devices"></a>Выход из системы для текущего пользователя на устройствах iOS, управляемых в Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Действие **Выход из системы для текущего пользователя** выполняет выход из системы для текущего пользователя на совместно используемом устройстве iPad. 

## <a name="supported-platforms"></a>Поддерживаемые платформы

- Windows — не поддерживается
- Windows Phone — не поддерживается
- iOS — поддерживается в iOS 9.3 и более поздних версиях (только общие устройства iPad)
- macOS — не поддерживается
- Android — не поддерживается

## <a name="how-to-log-out-the-current-user"></a>Выход текущего пользователя из системы

1. Зарегистрируйтесь на портале Azure.
2. Выберите **Больше служб** > **Мониторинг и управление** > **Intune**.
3. В колонке **Intune** выберите **Устройства**.
4. В колонке **Устройства и группы** выберите **Все устройства**.
5. Выберите нужное устройство iOS в списке управляемых устройств, а затем удаленное действие **Выход из системы для текущего пользователя**.

## <a name="next-steps"></a>Дальнейшие шаги

Чтобы просмотреть состояние выполненного действия, в колонке **Устройства и группы** выберите **Действия устройства**.