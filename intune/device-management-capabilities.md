---
title: Возможности управления устройствами в Microsoft Intune
description: В этом разделе содержатся сведения о том, как Intune может помочь в управлении зарегистрированными устройствами.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 22e184530dc0ae0e2bb636d3df8d5b45d8c4d0c7
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2018
ms.locfileid: "52189511"
---
# <a name="enrolled-device-management-capabilities-of-microsoft-intune"></a>Возможности управления зарегистрированными устройствами в Microsoft Intune

Microsoft Intune позволяет управлять различными устройствами путем их *регистрации* в службе. Можно зарегистрировать некоторые типы устройств самостоятельно, кроме того, устройства могут регистрировать пользователи с помощью приложения *корпоративного портала*. Регистрация позволяет просматривать и устанавливать приложения, проверять соответствие устройств политикам компании и обращаться в службу поддержки.

В этой статье приводится полный список возможностей, доступных после регистрации устройств.

Обработка операций управления, инвентаризации, развертывания приложений, подготовки и снятия с учета выполняется на портале Intune.

Пользователи получают доступ к корпоративному порталу, который позволяет им устанавливать приложения, регистрировать и удалять устройства, а также связываться с ИТ-отделом или службой поддержки.



## <a name="device-security-and-configuration"></a>Безопасность и конфигурация устройств

|Функция|Подробные сведения|Дополнительные сведения|
|--------------|-----------|--------------------|
|Политики конфигурации<br><br>Настраиваемые политики| Позволяют управлять многими параметрами и функциями на мобильных устройствах в организации. Например, можно требовать ввод пароля, ограничить число неудачных попыток входа, ограничить период бездействия до блокировки экрана, задать срок действия пароля и исключить использование прошлых паролей. Можно также контролировать использование функций оборудования и программного обеспечения, например камеры устройства или веб-браузера.<br><br>Настраиваемые политики рекомендуется использовать, если политики конфигурации не содержат необходимых параметров. Для устройств iOS можно импортировать параметры, экспортированные из средства Apple Configurator. Для других устройств можно использовать параметры OMA-URI для настройки параметров и функций на устройстве.|[Управление параметрами и компонентами на устройствах с помощью политик Microsoft Intune](device-compliance-get-started.md)|
|Удаленная очистка, удаленная блокировка и сброс пароля.|Удаление конфиденциальной информации при утере или краже устройства. Например, можно удаленно заблокировать устройство, восстановить заводские настройки или очистить только корпоративные данные.<br><br>Можно сбросить пароли, если пользователи потеряли доступ к устройству, заблокировать потерянные или украденные устройства и даже стереть данные на потерянных или украденных устройствах.|Защита устройств с помощью функций [удаленной блокировки](device-remote-lock.md) и [сброса секретного кода](device-passcode-reset.md)|
|Полноэкранный режим|Позволяет заблокировать некоторые возможности мобильных устройств, такие как снимок экрана и кнопка питания. Можно также запретить запуск на устройстве всех приложений, кроме одного указанного.|[Параметры политики конфигурации iOS в Microsoft Intune](device-restrictions-ios.md)|

## <a name="app-management"></a>Управление приложениями

|Функция|Подробные сведения|Дополнительные сведения|
|--------------|-----------|--------------------|
|Развертывание приложений и управление ими|Предоставляет широкий набор средств для управления мобильными приложениями в жизненном цикле, включая развертывание приложений из файлов установки и магазинов приложений, а также подробный мониторинг состояния приложений и их удаление.|[Развертывание приложений в Microsoft Intune](apps-deploy.md)|
|Compliant and noncompliant apps (Соответствующие и несоответствующие приложения)|Позволяет указать списки соответствующих приложений (которые пользователям разрешено устанавливать) и несоответствующих приложений (которые пользователям запрещено устанавливать).|[Параметры политики iOS в Microsoft Intune](device-restrictions-ios.md)|
|Mobile application management (Управление мобильными приложениями)|Ограничения для приложений настраиваются с помощью функции управления мобильными приложениями для устройств, управляемых и не управляемых Intune. Вы можете повысить безопасность данных компании путем запрета таких операций, как копирование и вставка, внешнее резервное копирование данных и передача данных между приложениями.|[Настройка и развертывание политик управления мобильными приложениями в консоли Microsoft Intune](app-wrapper-prepare-android.md)|
|Конфигурация мобильного приложения iOS|Политики конфигурации мобильных приложений используются для предоставления параметров приложениям iOS, которые могут быть необходимы, когда пользователь работает с приложением. Например, приложению может потребоваться, чтобы пользователь указал номер порта или данные для входа. Вы можете упростить конфигурацию приложения и сократить число обращений в службу поддержки.|[Настройка приложений iOS с помощью политик конфигурации мобильных приложений в Microsoft Intune](app-configuration-policies-use-ios.md)|
|Профили подготовки мобильных приложений iOS|Позволяют заранее развертывать профили подготовки в приложениях iOS, срок действия которых вскоре истекает. |[Предотвращение истечения срока действия сертификата мобильного приложения iOS с помощью политик профиля подготовки](app-provisioning-profile-ios.md)|
|Управляемый браузер|Настройка политик управляемого браузера для задания веб-сайтов, которые может посещать пользователь устройства. Кроме того, можно применять политики управления мобильными приложениями к управляемому браузеру.|[Управление доступом в Интернет с помощью политик управляемого браузера в Microsoft Intune](app-configuration-managed-browser.md)|
|Windows Hello для бизнеса|Поддерживает интеграцию с Windows Hello для бизнеса, являющeйся альтернативным методом входа для Windows 10, который использует локальный Active Directory или Azure Active Directory в качестве замены паролей, смарт-карт или виртуальных смарт-карт.|[Управление параметрами Windows Hello для бизнеса на устройствах с помощью Microsoft Intune](windows-hello.md)|
|Приложения, приобретенные по программе Volume Purchase Program|Помогает управлять приложениями, приобретенными по программе Volume Purchase Program, импортируя данные о лицензиях из магазина приложений, отслеживая число используемых лицензий и следя за тем, чтобы число установленных копий приложения не превышало число приобретенных.|[Управление приложениями, приобретенными по программе корпоративных закупок, с помощью Microsoft Intune](vpp-apps.md)|

## <a name="company-resource-access"></a>Доступ к ресурсам компании

|Функция|Подробные сведения|Дополнительные сведения|
|--------------|-----------|--------------------|
|Профили сертификатов|Создание и развертывание профилей доверенных сертификатов и сертификатов SCEP, которые можно использовать для защиты и проверки подлинности профилей Wi-Fi, VPN и электронной почты.|[Защита доступа к ресурсам с помощью профилей сертификатов в Microsoft Intune](certificates-configure.md)|
|Профили Wi-Fi|Развертывание параметров беспроводной сети для пользователей. Развертывание этих параметров упрощает подключение к корпоративной сети для конечных пользователей.|[Подключения Wi-Fi в Microsoft Intune](wi-fi-settings-configure.md)|
|Профили электронной почты|Создание и развертывание параметров почты на устройствах для предоставления пользователям доступа к корпоративной почте с личных устройств без дополнительных настроек с их стороны.|[Настройка доступа к корпоративной электронной почте с помощью профилей электронной почты с Microsoft Intune](email-settings-configure.md)|
|Профили VPN|Развертывание параметров VPN для пользователей и устройств в вашей организации. Развертывание этих параметров упрощает для конечного пользователя подключение к ресурсам в локальной сети.|[VPN-подключения в Microsoft Intune](device-profiles.md#vpn)|
|Политики условного доступа|Управление доступом к электронной почте Microsoft Exchange и SharePoint Online с устройств, которые не находятся под управлением Intune.|[Ограничение доступа к электронной почте и SharePoint с помощью Microsoft Intune](app-based-conditional-access-intune.md)|

## <a name="next-steps"></a>Дальнейшие шаги

[Просмотрите список устройств, которыми можно управлять](device-management.md).