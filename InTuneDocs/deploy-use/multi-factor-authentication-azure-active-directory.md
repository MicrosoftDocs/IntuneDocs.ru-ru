---
title: "Многофакторная проверка подлинности с помощью Azure AD | Документы Майкрософт"
description: "Как настроить обязательную многофакторную проверку подлинности в Azure AD для регистрации устройств."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angerobe
ms.date: 12/12/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 47abdabd-dcd6-48d8-aade-3f3eefb92ee1
ROBOTS: 
translationtype: Human Translation
ms.sourcegitcommit: 85462d6cb5e3dc6ce8e94fe8fd1bc1c1c2b6e4f3
ms.openlocfilehash: 6e20eca60886781ae884107a224245639c5f107c


---

# <a name="multi-factor-authentication-for-microsoft-intune"></a>Многофакторная проверка подлинности для Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune интегрирует многофакторную проверку подлинности (MFA) Azure AD при регистрации устройств для защиты корпоративных ресурсов. Многофакторная проверка подлинности требует использования факторов, таких как текстовая проверка подлинности, дополняющих имена пользователей и пароли. Эта возможность поддерживается на устройствах под управлением iOS, Android, Windows 8.1 и более поздних версий, а также Windows Phone 8.1 и более поздних версий.

> [!NOTE]
>
> Это новая процедура многофакторной проверки подлинности в Intune. Старая процедура описана в разделе [Защита устройств Windows с помощью многофакторной проверки подлинности в Intune](protect-windows-devices-with-multi-factor-authentication.md).
>
> В более ранних версиях Configuration Manager (до версии 1610) параметр многофакторной проверки подлинности все равно будет отображаться в консоли администрирования. Не пытайтесь настроить многофакторную проверку подлинности в консоли администрирования Configuration Manager. Она не будет работать. Настройте MFA, как описано в этой статье.

### <a name="configuring-intune-to-require-multi-factor-authentication-at-device-enrollment"></a>Настройка в Intune обязательной многофакторной проверки подлинности при регистрации устройств
Для обязательной многофакторной проверки подлинности при регистрации устройств выполните следующие действия.

1. Войдите на [портал Microsoft Azure](https://manage.windowsazure.com), используя свои учетные данные администратора.
2. Выберите клиент.
2. Выберите вкладку **Приложения**. Появится список служб, для которых можно настроить функции безопасности Azure AD.
3. Выберите **Microsoft Intune enrollment** (Регистрация в Microsoft Intune).
4. Выберите **Настройка**. 
5. В разделе **Многофакторная проверка подлинности и правила доступа на основе расположения** вы можете:
    
    -  Включить правила доступа.
    -  Выбрать, следует ли применять правила ко всем пользователям или к конкретным группам безопасности Azure AD.
    -  Настроить обязательную многофакторную проверку подлинности при регистрации всех устройств.
    -  Настроить обязательную многофакторную проверку подлинности при регистрации устройств не на рабочем месте.
    -  Для предотвращения регистрации устройства, не подключенного к корпоративной сети, выберите **Block access to corporate resources** (Заблокировать доступ к корпоративным ресурсам). 
4. Выбрав ссылку **Щелкните здесь, чтобы определить или изменить сетевое расположение работы**, вы сможете настроить требования к сетевому подключению для регистрации устройств.

> [!IMPORTANT]
> 
> Не устанавливайте **правила доступа на основе устройств** для регистрации в Microsoft Intune.



<!--HONumber=Dec16_HO3-->

