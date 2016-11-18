---
title: "Использование приложений с политиками управления мобильными приложениями | Microsoft Intune"
description: "Объяснение того, как MAM CA может помочь в управлении доступом приложений к службам Office 365."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 10/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 71dcf9bc-bfd1-4e06-b7ad-14b33a2288d0
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5083cb49e7a98f19ff21c1972149b00aee4ec93e
ms.openlocfilehash: f93dc1d57e87b17bb949de8ad5476dd8abc364d0


---
# Что произойдет при использовании приложения с MAM CA
MAM CA проверяет подлинность разрешенного приложения с помощью приложения посредника, которое должно иметься на устройстве:
*  В **iOS** приложением посредника является **Azure Authenticator**.
* В **Android** приложением посредника является **приложение корпоративного портала Intune**. 

Пользователям, которые впервые входят в приложение, поддерживаемое MAM CA, например OneDrive или Outlook, предлагается установить приложение посредника и зарегистрировать устройство в Azure AD. При регистрации устройства в Azure AD (ранее выполнялась с помощью Workplace Join) создаются запись устройства и сертификат, для которого выдаются маркеры.  Это **не** то же самое, что **регистрация MDM**. Здесь нет применяемых профилей управления или политик, а также списка приложений на устройстве.  Процесс установки приложения посредника и регистрации устройства произойдет только при первом использовании управляемого приложения.

Список свойств, которые наследуются непосредственно с устройства:

* alternativeSecurityIds (отпечаток сертификата Azure Active Directory и хэш открытого ключа)
* deviceOSType
* deviceOSVersion
* displayName


## MAM CA с условным доступом на основе соответствия устройств  

Можно настроить [условный доступ на основе соответствия устройств](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) (**Device CA**) в [консоли администрирования Intune](https://manage.microsoft.com) или [консоли управления Azure AD Premium] (https://manage.windowsazure.com). Device CA требует от пользователей подключаться к Exchange Online только с устройств, управляемых Intune, которые соответствуют требованиям политики соответствия устройств Intune, или с компьютеров, присоединенных к домену.  Если пользователь принадлежит к одной или нескольким группам безопасности, в отношении которых действуют политики MAM CA и Device CA, он должен соответствовать одному из двух требований:
* Приложение, используемое для доступа к службе, является мобильным приложением, поддерживаемым MAM CA, и на устройстве, на котором работает приложение, установлено приложение **iOS Authenticator (для устройств iOS)** или **приложение корпоративного портала (для устройств Android)**.
* Устройство, используемое для доступа к службе, **управляется Intune и соответствует** политике соответствия устройств Intune, либо является **компьютером, присоединенным к домену**.  Ниже приведены некоторые примеры.
  * Если пользователь пытается подключиться с **встроенного приложения электронной почты iOS**, он должен использовать **управляемое и соответствующее устройство**, поскольку встроенное почтовое приложение не поддерживается в MAM CA.
  * Если пользователь пытается подключиться с **домашнего компьютера Windows**, будет применяться **политика Device CA**, которая требует использовать компьютер, присоединенный к домену.




## Дальнейшие действия
[Создание политики Exchange Online для приложений MAM](mam-ca-for-exchange-online.md)

[Блокировка приложений, не поддерживающих современные средства проверки подлинности](block-apps-with-no-modern-authentication.md)

### См. также

[Защита данных приложения с помощью политик MAM](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Oct16_HO4-->

