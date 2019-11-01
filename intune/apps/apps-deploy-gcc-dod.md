---
title: Приложения для сред GCC High и DoD
titleSuffix: Microsoft Intune
description: Узнайте о развертывании приложений в средах GCC High и DoD с помощью Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 29329f86-1aa5-434f-9925-8dc28bf35348
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8a6c430ab15c40166e8c3afbccd6fcc7c2c5976d
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72507269"
---
# <a name="deploying-apps-using-intune-on-the-gcc-high-and-dod-environments"></a>Развертывание приложений в средах GCC High и DoD 

Администраторы клиентов могут использовать Microsoft Intune для распространения приложений для своих работников. Работники — это сотрудники компании, пользователи приложений. Существует много типов приложений, которые можно развернуть в средах GCC High или DoD с помощью Intune. Если администратору необходимо отправить и распространить приложение Windows, которое предназначено для пользователей в средах GCC High или DoD и является результатом собственной разработки, создано сторонним поставщиком или доступно в виде автономного приложения, скачанного из [Магазина Майкрософт для бизнеса](https://businessstore.microsoft.com/store), он может распространить его как [бизнес-приложение](apps-add.md#app-types-in-microsoft-intune).  

> [!NOTE]
> Для распространения в коммерческих средах администратор клиента может синхронизировать Магазин для бизнеса с Intune, но для сред GCC High и DoD сделать это невозможно. В таком случае администратору следует развернуть приложение, отправив его напрямую в Intune.  

## <a name="add-line-of-business-apps-using-intune"></a>Добавление бизнес-приложений с помощью Intune 

Чтобы добавить бизнес-приложение, предназначенное для сред GCC High и DoD, с помощью Intune, следуйте инструкциям [по добавлению бизнес-приложения Windows](lob-apps-windows.md). Сначала можно развернуть корпоративный портал из Магазина Майкрософт для бизнеса. Если вы решили использовать корпоративный портал, его можно установить и развернуть вручную. Дополнительные сведения см. в статье [Настройка приложения корпоративного портала Microsoft Intune](company-portal-app.md). 

## <a name="distribute-offline-apps-from-the-store-for-business-using-intune"></a>Распространение автономных приложений из Магазина для бизнеса с помощью Intune  

Чтобы [скачать автономно лицензированное приложение](https://docs.microsoft.com/microsoft-store/distribute-offline-apps#download-an-offline-licensed-app) из Магазина Майкрософт для бизнеса, выполните следующие действия. 

1. Войдите в [Магазин для бизнеса](https://businessstore.microsoft.com/).
2. Выберите **Управление** > **Параметры**.
3. В разделе **Shopping experience** (Совершение покупок) задайте параметру **Show offline apps** (Показать автономные приложения) значение **Вкл**.

Если при покупке доступна автономная версия приложения, можно изменить тип лицензии на автономный. Для управления приобретенным приложением выберите **Управление** > **Продукты и услуги** в [Магазине для бизнеса](https://businessstore.microsoft.com/). Кроме того, можно скачать приложение и его зависимости. Затем это скачанное приложение (и его зависимости) развертывается для пользователей с помощью Intune.  

## <a name="syncing-intune-to-the-store-for-business"></a>Синхронизация Intune с Магазином для бизнеса. 

В коммерческих (негосударственных) средах администратор может синхронизировать Intune с Магазином Майкрософт для бизнеса. Эта функция недоступна в средах для государственных организаций. Дополнительные сведения о различиях между Intune в коммерческих средах и Intune в средах для государственных организаций см. в статье [Описание службы Enterprise Mobility + Security для государственных организаций США](https://docs.microsoft.com/enterprise-mobility-security/solutions/ems-govt-service-description).  

Сведения о синхронизации Intune с учетной записью Магазина для бизнеса см. в статье [Управление приложениями, приобретенными в Магазине Майкрософт для бизнеса, с помощью Microsoft Intune](windows-store-for-business.md).  

## <a name="compliance"></a>Соответствие требованиям 

Анализируя целесообразность использования этих служб, изучайте заявления о конфиденциальности и соответствии требованиям для приложений и сравнивайте их с требованиями в области соответствия, безопасности и конфиденциальности, действующими в вашей организации.   

## <a name="next-steps"></a>Дальнейшие шаги

Дополнительные сведения о развертывании и назначении приложений см. в статье [Назначение приложений группам с помощью Microsoft Intune](apps-deploy.md).

 