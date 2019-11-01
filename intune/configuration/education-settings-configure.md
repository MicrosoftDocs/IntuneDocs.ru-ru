---
title: Добавление или настройка параметров образования в Microsoft Intune в Azure | Документация Майкрософт
description: Используйте приложение "Тестирование" в профиле конфигурации устройства на устройствах Windows 10 и более поздних версий в Microsoft Intune. Создайте профиль конфигурации с помощью параметров образования и введите URL-адрес тестового приложения, выберите способ входа пользователей, отслеживайте экран во время теста и разрешайте или запрещайте текстовые подсказки во время теста.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/10/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f78c628498624b62daf6c3ac597547851697c500
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72493338"
---
# <a name="use-the-take-a-test-app-on-windows-10-devices-in-microsoft-intune"></a>Использование приложения "Тестирование" на устройствах Windows 10 в Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Профили образования в Intune предназначены для учащихся, которые сдают тест или экзамен на устройствах. Эта функция включает в себя приложение **Тестирование** и параметры для добавления тестового URL-адреса, выбора способа входа конечных пользователей в тест и многое другое. Эта функция поддерживается на следующих платформах.

- Windows 10 и более поздней версии

Когда пользователь входит в систему, приложение "Тестирование" автоматически открывается вместе с введенным вами тестом. Никакие другие приложения не можно запустить на устройстве во время выполнения теста. Дополнительные сведения о приложении "Тестирование" см. в статье [Прохождение тестов в Windows 10](https://docs.microsoft.com/education/windows/take-tests-in-windows-10).

В этой статье перечислены действия по созданию профиля конфигурации устройства в Microsoft Intune. Она также содержит сведения для чтения и изучения доступных параметров образования для ваших устройств Windows 10.

## <a name="create-a-device-profile"></a>Создание профиля устройства

1. Войдите в [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Выберите **Конфигурация устройства** > **Профили** > **Создать профиль**.
3. Укажите следующие свойства.

    - **Имя**. Введите описательное имя для нового профиля.
    - **Описание** Введите описание профиля. Этот параметр является необязательным, но мы рекомендуем его использовать.
    - **Платформа**. Выберите **Windows 10 и более поздних версий**.
    - **Профиль**. Выберите **Профиль образования**.

4. Введите параметры, которые вы хотите настроить.

    - [Windows 10 и более поздних версий](education-settings-windows.md).

5. Щелкните **OK** > **Создать**, чтобы сохранить изменения.

После настройки параметров и создания профиль отображается в списке профилей. Теперь нам нужно [назначить этот профиль группам](device-profile-assign.md).

## <a name="next-steps"></a>Дальнейшие шаги

См. список параметров образования и их описания в статье [Configure the Take a Test app on Windows 10 devices using Intune](education-settings-windows.md) (Настройка приложения "Тестирование" на устройствах Windows 10 с помощью Intune).

[Назначьте профиль](device-profile-assign.md) и [отслеживайте его состояние](device-profile-monitor.md).