---
title: "Возможности управления зарегистрированными устройствами | Документы Майкрософт"
description: "В этом разделе содержатся сведения о том, как Intune может помочь в управлении зарегистрированными устройствами."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/12/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f23b3ee7-78da-4e53-9fc2-78e58401bcf9
ms.reviewer: angrobe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f268cf29461447306d0f5c3ca06d541d9a03a49d
ms.openlocfilehash: 898975338edcd3267fd47d62d23b35e295f0d99b


---
# <a name="enrolled-device-management-capabilities-of-microsoft-intune"></a>Возможности управления зарегистрированными устройствами в Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune позволяет управлять различными устройствами путем их *регистрации* в службе. Можно зарегистрировать некоторые типы устройств самостоятельно, кроме того, устройства могут регистрировать пользователи с помощью приложения *корпоративного портала*. Это также позволяет им выполнять такие операции, как просмотр и установка приложений, проверка и реализация соответствия устройств политикам организации и обращение в службу ИТ-поддержки.

В этом разделе приводится полный список возможностей, доступных после регистрации устройств.

Обработка операций управления, инвентаризации, развертывания приложений, подготовки и снятия с учета выполняется в консоли администрирования Intune. Пользователи получают доступ к корпоративному порталу, который позволяет им устанавливать приложения, регистрировать и удалять устройства, а также связываться с ИТ-отделом или службой поддержки.



## <a name="device-security-and-configuration"></a>Безопасность и конфигурация устройств

|Функция|Подробные сведения|Дополнительные сведения|
|--------------|-----------|--------------------|
|Политики конфигурации<br><br>Настраиваемые политики| Позволяют управлять многими параметрами и функциями на мобильных устройствах в организации. Например, можно требовать ввод пароля, ограничить число неудачных попыток входа, ограничить период бездействия до блокировки экрана, задать срок действия пароля и исключить использование прошлых паролей. Можно также контролировать использование функций оборудования и программного обеспечения, например камеры устройства или веб-браузера.<br><br>Настраиваемые политики рекомендуется использовать, если политики конфигурации не содержат необходимых параметров. Для устройств iOS можно импортировать параметры, экспортированные из средства Apple Configurator. Для других устройств можно использовать параметры OMA-URI для настройки параметров и функций на устройстве.|[Управление параметрами и компонентами на устройствах с помощью политик Microsoft Intune](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)<br />|
|Удаленная очистка, удаленная блокировка и сброс пароля.|Удаление конфиденциальной информации при утере или краже устройства. Например, можно удаленно заблокировать устройство, восстановить заводские настройки или очистить только корпоративные данные.<br><br>Можно сбросить пароли, если пользователи потеряли доступ к устройству, заблокировать потерянные или украденные устройства и даже стереть данные на потерянных или украденных устройствах.|[Защита устройств с помощью функций удаленной очистки и сброса секретного кода](/intune/deploy-use/use-remote-lock-and-passcode-reset-in-microsoft-intune) и [Снятие устройств с учета из системы управления Intune](/intune/deploy-use/retire-devices-from-microsoft-intune-management)|
|Полноэкранный режим|Позволяет заблокировать некоторые возможности мобильных устройств, такие как снимок экрана и кнопка питания. Можно также запретить запуск на устройстве всех приложений, кроме одного указанного.|[Параметры политики конфигурации iOS в Microsoft Intune](/intune/deploy-use/ios-policy-settings-in-microsoft-intune)|

## <a name="app-management"></a>Управление приложениями

|Функция|Подробные сведения|Дополнительные сведения|
|--------------|-----------|--------------------|
|Развертывание приложений и управление ими|Предоставляет широкий набор средств для управления мобильными приложениями в жизненном цикле, включая развертывание приложений из файлов установки и магазинов приложений, а также подробный мониторинг состояния приложений и их удаление.|[Развертывание приложений в Microsoft Intune](/intune/deploy-use/deploy-apps)|
|Compliant and noncompliant apps (Соответствующие и несоответствующие приложения)|Позволяет указать списки соответствующих приложений (которые пользователям разрешено устанавливать) и несоответствующих приложений (которые пользователям запрещено устанавливать).|[Параметры политики iOS в Microsoft Intune](/intune/deploy-use/ios-policy-settings-in-microsoft-intune)|
|Управление мобильными приложениями|Ограничения для приложений настраиваются с помощью функции управления мобильными приложениями для устройств, управляемых и не управляемых Intune. Это позволяет повысить безопасность данных организации путем запрета таких операций, как копирование и вставка, внешнее резервное копирование данных и передача данных между приложениями.|[Настройка и развертывание политик управления мобильными приложениями в консоли Microsoft Intune](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console)<br><br>[Создание и развертывание политик управления мобильными приложениями с помощью Microsoft Intune](/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)<br /><br />[Подготовка приложений iOS для управления мобильными приложениями с помощью средства Microsoft Intune App Wrapping Tool](/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)<br /><br />[Подготовка приложений Android для управления мобильными приложениями с помощью инструмента упаковки для приложений Microsoft Intune](/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)|
|Конфигурация мобильного приложения iOS|Политики конфигурации мобильных приложений используются для предоставления параметров приложениям iOS, которые могут быть необходимы, когда пользователь работает с приложением. Например, приложению может потребоваться, чтобы пользователь указал номер порта или данные для входа. Это позволит упростить конфигурацию приложения и сократить число обращений в службу поддержки.|[Настройка приложений iOS с помощью политик конфигурации мобильных приложений в Microsoft Intune](/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)|
|Профили подготовки мобильных приложений iOS|Позволяют заранее развертывать профили подготовки в приложениях iOS, срок действия которых вскоре истекает. |[Предотвращение истечения срока действия сертификата мобильного приложения iOS с помощью политик профиля подготовки](/intune/deploy-use/ios-mobile-app-provisioning-profiles)|
|Управляемый браузер|Настройка политик управляемого браузера для задания веб-сайтов, которые может посещать пользователь устройства. Кроме того, можно применять политики управления мобильными приложениями к управляемому браузеру.|[Управление доступом в Интернет с помощью политик управляемого браузера в Microsoft Intune](/intune/deploy-use/manage-internet-access-using-managed-browser-policies)|
|Windows Hello для бизнеса|Поддерживает интеграцию с Windows Hello для бизнеса, являющeйся альтернативным методом входа для Windows 10, который использует локальный Active Directory или Azure Active Directory в качестве замены паролей, смарт-карт или виртуальных смарт-карт.|[Управление параметрами Windows Hello для бизнеса на устройствах с помощью Microsoft Intune](/intune/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune)|
|Приложения, приобретенные по программе Volume Purchase Program|Помогает управлять приложениями, приобретенными по программе Volume Purchase Program, импортируя данные о лицензиях из магазина приложений, отслеживая число используемых лицензий и следя за тем, чтобы число установленных копий приложения не превышало число приобретенных.|[Управление приложениями, приобретенными по программе корпоративных закупок, с помощью Microsoft Intune](/intune/deploy-use/manage-volume-purchased-apps-in-microsoft-intune)|

## <a name="company-resource-access"></a>Доступ к ресурсам компании

|Функция|Подробные сведения|Дополнительные сведения|
|--------------|-----------|--------------------|
|Профили сертификатов|Создание и развертывание профилей доверенных сертификатов и сертификатов SCEP, которые можно использовать для защиты и проверки подлинности профилей Wi-Fi, VPN и электронной почты.|[Защита доступа к ресурсам с помощью профилей сертификатов в Microsoft Intune](/intune/deploy-use/secure-resource-access-with-certificate-profiles)|
|Профили Wi-Fi|Развертывание параметров беспроводной сети для пользователей. Развертывание этих параметров упрощает подключение к корпоративной сети для конечных пользователей.|[Подключения Wi-Fi в Microsoft Intune](/intune/deploy-use/wi-fi-connections-in-microsoft-intune)|
|Профили электронной почты|Создание и развертывание параметров электронной почты на устройствах. Это позволяет пользователям получать доступ к корпоративной почте с личных устройств без дополнительных настроек с их стороны.|[Настройка доступа к корпоративной электронной почте с помощью профилей электронной почты с Microsoft Intune](/intune/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune)|
|Профили VPN|Развертывание параметров VPN для пользователей и устройств в вашей организации. Развертывание этих параметров упрощает для конечного пользователя подключение к ресурсам в локальной сети.|[VPN-подключения в Microsoft Intune](/intune/deploy-use/vpn-connections-in-microsoft-intune)|
|Политики условного доступа|Управление доступом к электронной почте Microsoft Exchange и SharePoint Online с устройств, которые не находятся под управлением Intune.|[Ограничение доступа к электронной почте и SharePoint с помощью Microsoft Intune](/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)|

## <a name="inventory-and-reporting"></a>Инвентаризация и отчетность

|Функция|Подробные сведения|Дополнительные сведения|
|--------------|-----------|--------------------|
|Инвентаризация и отчетность|Поиск сведений об управляемых устройствах и программном обеспечении, используемом этими устройствами.|[Получение сведений об устройствах с помощью инвентаризации в Microsoft Intune](/intune/deploy-use/understand-your-devices-with-inventory-in-microsoft-intune)|


### <a name="see-also"></a>См. также
[Возможности управления компьютерами с ОС Windows в Microsoft Intune](windows-pc-management-capabilities-in-microsoft-intune.md)



<!--HONumber=Dec16_HO3-->

