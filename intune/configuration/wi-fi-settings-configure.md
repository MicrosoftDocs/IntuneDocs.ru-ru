---
title: Создание профиля Wi-Fi для устройств в Microsoft Intune в Azure | Документация Майкрософт
description: Создание профиля конфигурации Wi-Fi для устройств в Microsoft Intune. Создайте профили для Android, Android для бизнеса, Android для киосков, iOS, macOS, Windows 10 и более поздних версий, а также Windows Holographic for Business. С помощью этих профилей можно создать подключение Wi-Fi для использования сертификатов, выбрать тип EAP, указать метод аутентификации, включить прокси-сервер и многое другое.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a794d724fe162ad7d464760661fecb45bd874431
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506451"
---
# <a name="add-and-use-wi-fi-settings-on-your-devices-in-microsoft-intune"></a>Добавление и использование параметров Wi-Fi для устройств в Microsoft Intune

Wi-Fi — это технология беспроводной связи, которая используется многими мобильными устройствами для получения доступа к сети. Microsoft Intune включает встроенные параметры Wi-Fi, которые можно развернуть для пользователей и устройств в организации. Эта группа параметров называется профилем, который можно назначить разным пользователям и группам. Когда вы назначите профиль, пользователи смогут получать доступ к корпоративной сети Wi-Fi без дополнительной настройки.

Предположим, вы установили новую сеть Wi-Fi с именем Contoso Wi-Fi. Теперь вам нужно для всех устройств iOS настроить подключение к этой сети. Вот как это делается:

1. Создайте профиль Wi-Fi, содержащий параметры для подключения к беспроводной сети Contoso по Wi-Fi.
2. Назначьте профиль группе, которая включает всех пользователей с устройствами iOS.
3. Пользователи обнаружат новую сеть Contoso Wi-Fi в списке беспроводных сетей на устройстве. Пользователи смогут подключаться к сети, используя выбранный вами метод проверки подлинности.

В этой статье описано, как создать профиль Wi-Fi. Также здесь приведены ссылки с описанием разных параметров для каждой платформы.

## <a name="supported-device-platforms"></a>Поддерживаемые платформы устройств

Профили Wi-Fi поддерживают следующие платформы устройств:

- Android 4 и более поздней версии.
- Android для бизнеса и Android для киосков
- Устройства iOS 8.0 и более поздней версии
- macOS X 10.11 и более поздние версии;
- Windows 10 и более поздних версий, Windows 10 Mobile, Windows Holographic for Business

> [!NOTE]
> Для устройств под управлением Windows 8.1 вы можете импортировать конфигурацию Wi-Fi, экспортированную с другого устройства.

## <a name="create-a-device-profile"></a>Создание профиля устройства

1. В [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) последовательно выберите **Конфигурация устройств** > **Профили** > **Создать профиль**.
2. Укажите следующие свойства.

    - **Имя**. Введите описательное имя для нового профиля. Назначьте имена профилям, чтобы позже их можно было легко найти. Например, хорошее имя профиля — **Профиль Wi-Fi для всей компании**.
    - **Описание** Введите описание профиля. Этот параметр является необязательным, но мы рекомендуем его использовать.
    - **Платформа**. Выберите платформу устройств. Доступны следующие параметры:

      - **Android**
      - **Android Enterprise**
      - **iOS/iPadOS**
      - **macOS**
      - **Windows 8.1 и более поздние версии**
      - **Windows 10 и более поздних версий**.

    - **Тип профиля**: выберите **Wi-Fi**.

      > [!TIP]
      >
      > - Для устройств **Android для бизнеса**, работающих в качестве выделенного устройства (киоск), выберите **Только владелец устройства** > **Wi-Fi**.
      > - Для **Windows 8.1 и более поздних версий** можно выбрать действие **Импорт Wi-Fi**. Этот вариант позволяет импортировать параметры Wi-Fi из XML-файла, который ранее был экспортирован с другого устройства.

3. Некоторые параметры Wi-Fi будут разными для разных платформ. Чтобы просмотреть параметры для конкретной платформы, выберите свою платформу:

    - [Android](wi-fi-settings-android.md)
    - [Android для бизнеса](wi-fi-settings-android-enterprise.md), включая выделенные устройства;
    - [iOS/iPadOS](wi-fi-settings-ios.md)
    - [macOS](wi-fi-settings-macos.md)
    - [Windows 10 и более поздних версий](wi-fi-settings-windows.md).
    - [Параметры Windows 8.1 и более поздних версий](wi-fi-settings-import-windows-8-1.md) (включая Windows Holographic for Business)

4. Когда все будет готово, выберите **Создать профиль** > **Создать**.

Созданный профиль отобразится в списке профилей (**Конфигурация устройства** > **Профили**).

## <a name="next-steps"></a>Дальнейшие шаги

Мы создали профиль, но он пока ничего не делает. Далее [назначьте профиль](device-profile-assign.md) и [отслеживайте его состояние](device-profile-monitor.md).