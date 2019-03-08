---
title: Параметры образования для Windows 10 в Microsoft Intune в Azure | Документация Майкрософт
description: Просмотрите список всех параметров образования для устройств Windows 10. Используйте эти параметры в профиле конфигурации устройства с приложением "Тестирование", выберите способ входа пользователей или учащихся, отслеживайте экран во время теста и многое другое в Intune.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 32c15037bad21ca90f81ed239ac24a9bac8d7499
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/02/2019
ms.locfileid: "57228329"
---
# <a name="configure-the-take-a-test-app-on-windows-10-devices-using-intune"></a>Настройка приложения "Тестирование" на устройствах Windows 10 с помощью Microsoft Intune

В этой статье описаны все параметры приложения образования "Тестирование" в Microsoft Intune, которые можно настроить для устройств под управлением Windows 10 и более поздних версий. С помощью этого приложения учащиеся могут войти на устройство и выполнить тест.

Эти параметры можно добавить в профиль конфигурации устройства, а затем назначить или развернуть на устройствах Windows 10 с помощью Microsoft Intune.

[Настройка параметров образования Windows 10 в Microsoft Intune](education-settings-configure.md) содержит дополнительные сведения об этой функции.

## <a name="before-you-begin"></a>Подготовка к работе

[Создайте профиль конфигурации устройства](education-settings-configure.md#create-a-device-profile).

## <a name="take-a-test-settings"></a>Параметры тестирования

- **Тип учетной записи**. Выберите, каким образом пользователи входят в тест. Доступны следующие параметры:
  - учетная запись Azure AD;
  - Доменная учетная запись
  - локальная учетная запись.
- **Имя пользователя учетной записи**. Введите имя пользователя учетной записи, используемой в приложении "Тестирование". Учетные записи можно ввести в следующем формате.
  - `user@contoso.com`
  - `domain\username`
  - `user@contoso.com`
  - `computerName\username`
- **URL-адрес оценки**. Укажите URL-адрес теста, который необходимо выполнять пользователям. Дополнительные сведения о получении URL-адреса см. в статье [Прохождение тестов в Windows 10](https://docs.microsoft.com/education/windows/take-tests-in-windows-10).
- **Мониторинг экрана**. Выберите **Разрешить**, чтобы отслеживать активность экрана во время прохождения теста пользователями. **Не настроено** — предотвращает наблюдение за экраном во время теста.
- **Предложение текста**. Выберите **Разрешить**, чтобы тестируемые могли видеть текстовые предложения. **Не настроено** — блокирует текстовые подсказки во время тестирования пользователями.

## <a name="next-steps"></a>Дальнейшие шаги

Профиль создан, но пока в нем ничего нельзя делать. Обязательно изучите статьи [Назначение профилей пользователей и устройств в Microsoft Intune](device-profile-assign.md) и [Мониторинг профилей устройств в Microsoft Intune](device-profile-monitor.md).