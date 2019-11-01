---
title: Параметры VPN для устройств Windows Phone 8.1 в Microsoft Intune
titleSuffix: ''
description: Сведения о параметрах Intune, используемых для настройки VPN-подключений на устройствах Windows Phone 8.1.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 69de660e65ed2a0f3b6c9c7e4ce774a6fcde2676
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506516"
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-windows-phone-81"></a>Настройка параметров VPN для устройств Windows Phone 8.1 в Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Сведения о параметрах Intune, используемых для настройки VPN-подключений на устройствах Windows Phone 8.1.


В зависимости от выбранных параметров не все приведенные в следующем списке значения будут доступны для настройки.

## <a name="base-vpn-settings"></a>Основные параметры VPN

- **Apply all settings to Windows Phone 8.1 only** (Применение всех параметров только к устройствам с Windows Phone 8.1). Этот параметр можно настроить на классическом портале Intune. На портале Azure этот параметр изменить невозможно. Если задано значение **Настроено**, все параметры применяются только к устройствам Windows Phone 8.1. Если выбрать значение **Не настроено**, эти параметры также применяются к устройствам Windows 10 Mobile.
- **Имя подключения.** Введите имя подключения. Пользователи видят это имя при поиске устройства в списке доступных VPN-подключений.
- **Способ проверки подлинности.** Укажите, как устройства будут проходить проверку подлинности на VPN-сервере.
  - **Сертификаты.** В разделе **Сертификат проверки подлинности** выберите профиль сертификата SCEP или PKCS, созданный ранее для проверки подлинности подключения. Дополнительные сведения о профилях сертификатов см. в статье о [настройке сертификатов с помощью Microsoft Intune](../protect/certificates-configure.md).
  - **Имя пользователя и пароль**. Конечным пользователям необходимо ввести имя пользователя и пароль для входа на VPN-сервер.
- **Серверы**. Добавьте один или несколько VPN-серверов, к которым подключаются устройства.
  - **Добавить**. Открывает колонку **Добавить строку**, в которой можно указать перечисленные ниже сведения:
    - **Описание**. Укажите описательное имя сервера, например **VPN-сервер Contoso**.
    - **IP-адрес или полное доменное имя**. Укажите IP-адрес или полное доменное имя VPN-сервера, к которому подключаются устройства. Примеры: **192.168.1.1**, **vpn.contoso.com**.
    - **Сервер по умолчанию**. Позволяет использовать данный сервер как сервер по умолчанию, который устройства используют для установки подключения. Обязательно установите только один сервер в качестве сервера по умолчанию.
  - **Импорт**. Найдите файл, содержащий список серверов с указанными через запятую следующими данными: описание, IP-адрес или полное доменное имя, сервер по умолчанию. Щелкните **ОК**, чтобы импортировать эти параметры в список **Серверы**.
  - **Экспорт**. Экспортирует список серверов в файл данных с разделителями-запятыми (CSV-файл).

- **Обходить VPN в сети Wi-Fi организации**. Выберите этот параметр, чтобы указать, что VPN-подключение не будет использоваться, когда устройство подключено к сети Wi-Fi организации.
- **Обходить VPN в домашней сети Wi-Fi**. Выберите этот параметр, чтобы указать, что VPN-подключение не будет использоваться, когда устройство подключено к домашней сети Wi-Fi.

- **Тип подключения**. Выберите тип VPN-подключения в следующем списке поставщиков:
  - **Check Point Capsule VPN**;
  - **SonicWall Mobile Connect**;
  - **F5 Edge Client**
  - **Pulse Secure**

- **Домен или группа входа** (только для SonicWall Mobile Connect). Укажите имя группы входа или домена, к которым следует подключиться.
- **Роль** (только Pulse Secure). Укажите имя роли пользователя, имеющего доступ к этому подключению. Роль пользователя определяет личные настройки и параметры, а также включает или отключает определенные функции доступа.
- **Область** (только Pulse Secure). Укажите имя области проверки подлинности, которую следует использовать. Область аутентификации — это группа ресурсов аутентификации, которая используется типом подключения Pulse Secure.

- **Список поиска DNS-суффиксов**.**Добавьте** один или несколько DNS-суффиксов. При подключении к веб-сайту с использованием короткого имени будет выполнен поиск каждого указанного DNS-суффикса. Например, укажите DNS-суффиксы **domain1.contoso.com** и **domain2.contoso.com**, перейдите по URL-адресу `http://mywebsite` для поиска URL-адресов `http://mywebsite.domain1.contoso.com` и `http://mywebsite.domain2.contoso.com`.

- **Настраиваемый XML**. Укажите любые пользовательские команды XML, настраивающие VPN-подключение.

    **Пример для Pulse Secure:**

```xml
    <pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

**Пример для CheckPoint Mobile VPN:**

```xml
    <CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

**Пример для SonicWall Mobile Connect:**

```xml
<MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

**Пример для F5 Edge Client:**

```xml
    <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

Дополнительные сведения о создании пользовательских команд XML см. в документации VPN каждого производителя.

- **Разделить туннелирование** - . Выберите **Включить** или **Отключить** этот параметр, позволяющий устройствам выбрать нужное подключение в зависимости от трафика. Например, пользователь в отеле использует VPN-подключение для доступа к рабочим файлам, а стандартную сеть отеля — для обычного просмотра веб-страниц.




## <a name="proxy-settings"></a>Параметры прокси-сервера

- **Автоматическое определение параметров прокси-сервера.** Если VPN-серверу требуется прокси-сервер для подключения, укажите, следует ли устройствам автоматически определять параметры подключения. Дополнительные сведения см. в документации по Windows Server.
- **Скрипт автоматической настройки.** Используйте файл для настройки прокси-сервера. Введите **URL-адрес прокси-сервера** (например, `http://proxy.contoso.com`), на котором находится файл конфигурации.
- **Использовать прокси-сервер**. Включите этот параметр, если требуется ввести параметры прокси-сервера вручную.
  - **Адрес**. Введите адрес прокси-сервера (в формате IP-адреса).
  - **Номер порта.** Введите номер порта, связанного с прокси-сервером.
- **Обходить прокси-сервер для локальных адресов.** Если VPN-серверу требуется прокси-сервер для подключения, выберите этот параметр, если вы не хотите использовать прокси-сервер для указанных локальных адресов. Дополнительные сведения см. в документации по Windows Server.