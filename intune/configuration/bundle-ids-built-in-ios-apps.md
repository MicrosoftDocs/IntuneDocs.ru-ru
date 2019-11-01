---
title: Идентификаторы пакета iOS для встроенных приложений в Microsoft Intune — Azure | Документация Майкрософт
titleSuffix: ''
description: Ознакомьтесь со списком идентификаторов пакетов для встроенных приложений iOS. Используйте эти идентификаторы пакетов, чтобы явно разрешить приложения в профилях и политиках конфигурации устройств в Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/30/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: ''
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1eda7fef3ee9c2ca4e4a13d9b6effba2ed121b0e
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506955"
---
# <a name="bundle-ids-for-built-in-ios-apps-you-can-use-in-intune"></a>Идентификаторы пакетов для встроенных приложений iOS, которые можно использовать в Intune

При настройке возможностей на устройствах iOS можно также добавить встроенные приложения на устройствах iOS. В этой статье перечислены идентификаторы пакета некоторых стандартных встроенных приложений iOS. Чтобы найти идентификаторы наборов других приложений, обратитесь к поставщику программного обеспечения. См. список [идентификаторов пакета iOS](https://support.apple.com/guide/mdm/ios-bundle-ids-mdm90f60c1ce/web) от Apple (веб-сайт Apple).

## <a name="bundle-ids"></a>Идентификаторы пакета

| Идентификатор пакета                   | имя приложения;     | Издатель |
|-----------------------------|--------------|-----------|
| com. Apple. Store             | Магазин App Store    | Apple     |
| com.apple.calculator        | "Калькулятор"   | Apple     |
| com.apple.mobilecal         | "Календарь"     | Apple     |
| com.apple.camera            | Камера       | Apple     |
| com.apple.mobiletimer       | "Часы"        | Apple     |
| com. Apple. зажимы             | Clips        | Apple     |
| com.apple.compass           | "Компас"      | Apple     |
| com.apple.MobileAddressBook | "Контакты"     | Apple     |
| com.apple.facetime          | FaceTime     | Apple     |
| com.apple.DocumentsApp      | Файлы        | Apple     |
| com.apple.mobileme.fmf1     | "Найти друзей" | Apple     |
| com.apple.mobileme.fmip1    | "Найти iPhone"  | Apple     |
| com.apple.gamecenter        | Game Center  | Apple     |
| com.apple.mobilegarageband  | GarageBand   | Apple     |
| com.apple.Health            | "Здоровье"       | Apple     |
| com.apple.Home              | Корневая         | Apple     |
| com.apple.iBooks            | iBooks       | Apple     |
| com.apple.iMovie            | iMovie       | Apple     |
| com.apple.itunesconnect.mobile | iTunes Connect | Apple |
| com.apple.MobileStore       | Магазин iTunes | Apple     |
| com.apple.itunesu           | iTunes U     | Apple     |
| com.apple.Keynote           | Keynote      | Apple     |
| com.apple.mobilemail        | Mail         | Apple     |
| com.apple.Maps              | "Карты"         | Apple     |
| com.apple.MobileSMS         | "Сообщения"     | Apple     |
| com.apple.Music             | "Музыка"        | Apple     |
| com.apple.news              | News         | Apple     |
| com.apple.mobilenotes       | "Заметки"        | Apple     |
| com.apple.Numbers           | Numbers      | Apple     |
| com.apple.Pages             | Pages        | Apple     |
| com.apple.mobilephone       | Телефон        | Apple     |
| com.apple.Photo-Booth       | Photo Booth  | Apple     |
| com.apple.mobileslideshow   | Фотографии       | Apple     |
| com.apple.podcasts          | "Подкасты"     | Apple     |
| com.apple.reminders         | "Напоминания"    | Apple     |
| com.apple.mobilesafari      | Safari       | Apple     |
| com.apple.Preferences       | "Настройки"     | Apple     |
| com.apple.SiriViewService   | Siri         | Apple     |
| com.apple.stocks            | "Акции"       | Apple     |
| com.apple.tips              | "Советы"         | Apple     |
| com.apple.tv                | TV           | Apple     |
| com.apple.videos            | Видео       | Apple     |
| com.apple.VoiceMemos        | VoiceMemos   | Apple     |
| com.apple.Passbook          | Wallet       | Apple     |
| com.apple.Bridge            | Watch        | Apple     |
| com.apple.weather           | "Погода"      | Apple     |      

## <a name="next-steps"></a>Дальнейшие шаги

Используйте эти идентификаторы пакета, чтобы настроить [функции устройства](ios-device-features-settings.md), а также чтобы [разрешить или ограничить некоторые параметры](device-restrictions-ios.md) на устройствах iOS.