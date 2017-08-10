---
title: "Политика | Документация Майкрософт"
description: "Справочник по категории \"Политика\" коллекций сущностей в API хранилища данных Intune."
keywords: "Хранилище данных Intune"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: D5ADB9D8-D46A-43BD-AB0F-D6927508E3F4
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 6af0ff1f463c153e62f6df63ce811076c5f692f2
ms.sourcegitcommit: addf6a40caa22c22adfd2e2eff7d666cd1877e3c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2017
---
# <a name="reference-for-policy-entities"></a>Справочник по сущностям политики

Категория **Политика** содержит сущности для мобильных устройств, отслеживающие указанную ниже информацию:

  -  Инвентаризация профилей конфигурации устройств, профилей конфигурации приложений и политик соответствия требованиям  
  -  Число устройств с состоянием успешного выполнения, ожидания, неудачного выполнения или ошибки в день  
  -  Число пользователей с состоянием успешного выполнения, ожидания, неудачного выполнения или ошибки в день  
  -  Совокупное число устройств с состоянием успешного выполнения, ожидания, неудачного выполнения или ошибки  

## <a name="policy"></a>Политика

Сущность **Policy** перечисляет профили конфигурации устройств, профили конфигурации приложений и политики соответствия требованиям. Вы можете назначить политики группе в вашей организации с помощью управления мобильными устройствами (MDM).

| Свойство  | Описание | Пример |
|---------|------------|--------|
| PolicyKey |Уникальный ключ для представления политики в хранилище данных |123 |
| PolicyId |Уникальный идентификатор политики в хранилище данных |b66bc706-ffff-7437-0340-032819502773 |
| PolicyName |Имя политики |"Windows 10 Baseline" |
| PolicyVersion |Версия политики. При изменении политики создается более новая версия. |1, 2, 3 |
| IsDeleted |Указывает, обновлена ли запись политики.  True — политика имеет новую запись с обновленными полями. False — последняя запись для этой политики. |Истина/ложь |
| StartDateInclusiveUTC |Дата и время (в формате UTC) создания этой политики в хранилище данных |23/11/2016 12:00:00 |
| DeletedDateUTC |Дата и время (в формате UTC), когда значение IsDeleted изменилось на True |23/11/2016 12:00:00 |
| RowLastModifiedDateTimeUTC |Дата и время (в формате UTC) последнего изменения этой политики в хранилище данных |23/11/2016 12:00:00 |

## <a name="policytype"></a>PolicyType

Сущность **PolicyType** перечисляет типы профилей конфигурации устройств, профилей конфигурации приложений и политик соответствия требованиям. Вы можете назначить политики группе в вашей организации с помощью управления мобильными устройствами (MDM).

| Свойство  | Описание | Пример |
|---------|------------|--------|
| PolicyTypeId |Уникальный идентификатор политики в исходной системе |123 |
| PolicyTypeKey |Уникальный идентификатор политики в хранилище данных |1 |
| PolicyTypeName |Имя типа политики |Windows 10 Compliance policy |

## <a name="deviceconfiguration"></a>DeviceConfiguration

Сущность **DeviceConfigurationProfileDeviceActivity** указывает число устройств с состоянием успешного выполнения, ожидания, неудачного выполнения или ошибки в день. Это число отражает профили конфигурации устройств, назначенные для сущности. Например, если устройство находится в состоянии успешного выполнения для всех назначенных ему политик, оно на единицу увеличивает счетчик Succeeded за этот день. Если устройству назначено два профиля, один из которых находится в состоянии успешного выполнения, а другой — в состоянии ошибки, эта сущность увеличивает счетчик Succeeded и переводит устройство в состояние ошибки. Сущность указывает, сколько устройств находится в определенном состоянии в заданный день за последние 30 дней.

| Свойство  | Описание | Пример |
|---------|------------|--------|
| DateKey |Ключ даты, когда в хранилище данных была записана отметка профиля конфигурации устройства |20160703 |
| Pending |Число уникальных устройств в состоянии ожидания |123 |
| успешно |Число уникальных устройств в состоянии успешного выполнения |12 |
| Ошибка |Число уникальных устройств в состоянии ошибки |10 |
| Failed |Число уникальных устройств в состоянии неудачного выполнения |2 |

## <a name="userconfiguration"></a>UserConfiguration

Сущность **UserConfigurationProfileDeviceActivity** указывает число пользователей с состоянием успешного выполнения, ожидания, неудачного выполнения или ошибки в день. Это число отражает профили конфигурации устройств, назначенные для сущности. Например, если пользователь находится в состоянии успешного выполнения для всех назначенных ему политик, он на единицу увеличивает счетчик Succeeded за этот день. Если пользователю назначено два профиля, один из которых находится в состоянии успешного выполнения, а другой — в состоянии ошибки, этот пользователь учитывается в счетчике состояния ошибки.  Сущность **UserConfigurationProfileDeviceActivity** указывает, сколько пользователей находится в определенном состоянии в заданный день за последние 30 дней.

| Свойство  | Описание | Пример |
|---------|------------|--------|
| DateKey |Ключ даты, когда в хранилище данных была записана отметка профиля конфигурации устройства |20160703 |
| Pending |Число уникальных пользователей в состоянии ожидания |123 |
| успешно |Число уникальных пользователей в состоянии успешного выполнения |12 |
| Ошибка |Число уникальных пользователей в состоянии ошибки |10 |
| Failed |Число уникальных пользователей в состоянии неудачного выполнения |2 |

## <a name="policytypeactivity"></a>PolicyTypeActivity

Сущность **PolicyTypeActivity** указывает совокупное число устройств с состоянием успешного выполнения, ожидания, неудачного выполнения или ошибки. Она указывает эти состояния с учетом профиля конфигурации устройства, профиля конфигурации приложения или политики соответствия требованиям за день.

| Свойство  | Описание | Пример |
|---------|------------|--------|
| DateKey |Ключ даты, когда в хранилище данных была записана отметка профиля конфигурации устройства |20160703 |
| PolicyKey |Ключ политики, который можно объединить с политикой для получения policyName |Windows 10 baseline |
| PolicyTypeKey |Тип ключа политики, который можно объединить с типом политики для получения имени типа политики |Windows10Compliance Policy |
| Pending |Число уникальных устройств в состоянии ожидания |123 |
| успешно |Число уникальных устройств в состоянии успешного выполнения |12 |
| Ошибка |Число уникальных устройств в состоянии ошибки |10 |
| Fail- |Число уникальных устройств в состоянии неудачного выполнения |2 |