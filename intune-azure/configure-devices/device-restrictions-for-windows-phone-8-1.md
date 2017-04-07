---
title: "Параметры ограничений Intune для применения к устройствам Windows Phone 8.1"
titleSuffix: Intune Azure preview
description: "Предварительная версия Intune Azure. Узнайте о параметрах Intune, с помощью которых можно управлять параметрами и функциональными возможностями устройств с Windows Phone 8.1."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c2d42714-49ca-43b3-b080-2e67a4268198
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 175401f05b10e7c8fdece996403832490e102a98
ms.lasthandoff: 02/18/2017


---

# <a name="windows-phone-81-device-restriction-settings-in-microsoft-intune"></a>Параметры ограничений для устройств с Windows Phone 8.1 в Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="general"></a>Общие
-     **Apply all settings to Windows Phone 8.1 only** (Применение всех параметров только к устройствам с Windows Phone 8.1). Этот параметр можно настроить на классическом портале Intune. На портале Azure этот параметр изменить невозможно. Если задано значение **Настроено**, все параметры будут применяться только к устройствам Windows Phone 8.1. Если выбрать значение **Не настроено**, эти параметры будут также применены к устройствам Windows 10 Mobile.
-     **Камера.** Разрешает или запрещает использовать камеру устройства.
-     **Копирование и вставка.** Разрешает или блокирует функции копирования и вставки на устройствах.
-     **Съемные носители.** Разрешает устройству использовать съемные носители, например SD-карты.
-     **Геолокация.** Разрешает устройству использовать сведения о расположении.
-     **Microsoft account** (Учетная запись Майкрософт). Разрешает или блокирует возможность пользователя связывать учетную запись Майкрософт с устройством.
-     **Снимок экрана.** Позволяет пользователю записывать содержимое экрана в виде файла изображения.
-     **Передача диагностических данных.** Разрешает устройству отправлять диагностические сведения в корпорацию Майкрософт.
-     **Синхронизация настраиваемых учетных записей электронной почты.** Разрешает устройству подключаться к сторонним учетным записям электронной почты.

## <a name="password"></a>Пароль
-     **Apply all settings to Windows Phone 8.1 only** (Применение всех параметров только к устройствам с Windows Phone 8.1). Этот параметр можно настроить на классическом портале Intune. На портале Azure этот параметр изменить невозможно. Если задано значение **Настроено**, все параметры будут применяться только к устройствам Windows Phone 8.1. Если выбрать значение **Не настроено**, эти параметры будут также применены к устройствам Windows 10 Mobile.
-     **Требуется пароль**. Пользователь должен ввести пароль для доступа к устройству.
    -     **Требуемый тип пароля.** Указывает необходимый тип пароля, например буквенно-цифровой или цифровой.
    -     **Минимальная длина пароля.** Указывает минимальное число символов в пароле.
    -     **Простые пароли.** Указывает, можно ли использовать простые пароли, такие как&0000; и&1234;.
    -     **Число неудачных попыток входа перед очисткой устройства.** Задает количество попыток ввода неверного пароля, прежде чем устройство будет очищено.
    -     **Максимальное время бездействия (в минутах), по истечении которого экран блокируется.** Указывает период бездействия устройства, по истечении которого экран автоматически блокируется.
    -     **Окончание срока действия пароля (в днях).** Указывает количество дней до смены пароля на устройстве.
    -     **Запретить использование предыдущих паролей.** Указывает количество предыдущих паролей.
-     **Шифрование.** Включает шифрование данных на поддерживаемых мобильных устройствах.

## <a name="app-store"></a>Магазин App Store
-     **Apply all settings to Windows Phone 8.1 only** (Применение всех параметров только к устройствам с Windows Phone 8.1). Этот параметр можно настроить на классическом портале Intune. На портале Azure этот параметр изменить невозможно. Если задано значение **Настроено**, все параметры будут применяться только к устройствам Windows Phone 8.1. Если выбрать значение **Не настроено**, эти параметры будут также применены к устройствам Windows 10 Mobile.
-     **App Store.** Позволяет пользователям подключаться к магазину приложений с устройства.

## <a name="restricted-apps"></a>Ограниченные приложения

-     **Apply all settings to Windows Phone 8.1 only** (Применение всех параметров только к устройствам с Windows Phone 8.1). Этот параметр можно настроить на классическом портале Intune. На портале Azure этот параметр изменить невозможно. Если задано значение **Настроено**, все параметры будут применяться только к устройствам Windows Phone 8.1. Если выбрать значение **Не настроено**, эти параметры будут также применены к устройствам Windows 10 Mobile.

В списке ограниченных приложений можно настроить один из следующих списков.

Список **Заблокированные приложения**. Содержит приложения, не управляемые Intune, которые пользователям запрещено устанавливать и запускать.
Список **Разрешенные приложения**. Содержит приложения, которые пользователям разрешено устанавливать. Приложения под управлением Intune автоматически разрешены.

Чтобы настроить список, щелкните **Добавить**, затем укажите выбранное имя, при необходимости издателя приложения и URL-адрес для приложения в магазине приложений.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Как указать URL-адрес для приложений в магазине

URL-адрес приложения в списке разрешенных и заблокированных приложений необходимо указывать в следующем формате:

На странице [Магазин Windows Phone](https://www.microsoft.com/store/apps/windows-phone) найдите приложение, которое вы хотите использовать.

Откройте страницу приложения и скопируйте URL-адрес в буфер обмена. После этого его можно использовать как URL-адрес в списке разрешенных приложений или в списке заблокированных приложений.

Пример. Выполните поиск в магазине по запросу "Приложение Skype". Нужный URL-адрес будет следующим: **http://www.windowsphone.com/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51**.



### <a name="additional-options"></a>Дополнительные параметры

Вы также можете щелкнуть **Импорт**, чтобы заполнить список из CSV-файла в формате <*URL-адрес приложения*>, <*имя приложения*>, <*издатель приложения*>, или **Экспорт**, чтобы создать CSV-файл, содержащий список ограниченных приложений в том же формате.


## <a name="browser"></a>Браузер
-     **Apply all settings to Windows Phone 8.1 only** (Применение всех параметров только к устройствам с Windows Phone 8.1). Этот параметр можно настроить на классическом портале Intune. На портале Azure этот параметр изменить невозможно. Если задано значение **Настроено**, все параметры будут применяться только к устройствам Windows Phone 8.1. Если выбрать значение **Не настроено**, эти параметры будут также применены к устройствам Windows 10 Mobile.
-     **Веб-браузер.** Разрешает или запрещает использовать встроенный веб-браузер на устройствах.

## <a name="cellular-and-connectivity"></a>Сотовая сеть и подключение
-     **Apply all settings to Windows Phone 8.1 only** (Применение всех параметров только к устройствам с Windows Phone 8.1). Этот параметр можно настроить на классическом портале Intune. На портале Azure этот параметр изменить невозможно. Если задано значение **Настроено**, все параметры будут применяться только к устройствам Windows Phone 8.1. Если выбрать значение **Не настроено**, эти параметры будут также применены к устройствам Windows 10 Mobile.
-     **Wi-Fi.** Включает или отключает функции Wi-Fi устройства.
-     **Модем Wi-Fi.** Разрешает использовать модем Wi-Fi в устройстве.
-     **Автоматически подключаться к хот-спотам Wi-Fi.** Разрешает устройству автоматически подключаться к бесплатным хот-спотам Wi-Fi и автоматически принимать любые условия использования.
-     **Отчеты по хот-спотам Wi-Fi.** Отправляет сведения о подключениях Wi-Fi, чтобы упростить поиск ближайших точек подключения.
-     **NFC.** Включает или отключает операции, которые используют радиочастотную связь ближнего действия на устройствах, поддерживающих эту связь.
-     **Bluetooth.** Включает или отключает функции Bluetooth на устройстве.
