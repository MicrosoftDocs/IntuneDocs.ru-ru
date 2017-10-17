---
title: "Интеграция Zimperium с Intune"
titleSuffix: Intune on Azure
description: "Интеграция Intune с Zimperium"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 09/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 363fd280-1865-4a61-855b-eb75c3c62753
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1b4adb2db14c2e1c83be8e7b3644944c1910cb97
ms.sourcegitcommit: d434dfab7ef7a6c4082d675717fa22d5581b4f51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2017
---
# <a name="integrate-zimperium-with-intune"></a>Интеграция Zimperium с Intune

Необходимо выполнить следующие действия, чтобы интегрировать решение Mobile Threat Defense Zimperium с Intune.

## <a name="before-you-begin"></a>Подготовка к работе

> [!NOTE]
> Приведенные ниже действия необходимо выполнить [в консоли MTD Zimperium](https://staging2-console.zimperium.com).

Перед началом интеграции Zimperium с Intune убедитесь в наличии следующего:

-   Подписка Microsoft Intune

-   Учетные данные администратора Azure Active Directory для предоставления следующих разрешений:

    -   Вход и чтение профилей пользователей

    -   Доступ к каталогу от имени вошедшего в систему пользователя

    -   Чтение данных каталога

    -   Отправка сведений об устройстве в Intune

-   Учетные данные администратора для доступа к консоли MTD Zimperium.

### <a name="zimperium-app-authorization"></a>Авторизация приложения Zimperium

Авторизация приложения Zimperium выполняется следующим образом.

-   Вы разрешаете службе Zimperium передавать в Intune сведения о состоянии работоспособности устройства.

-   Zimperium синхронизируется с членством в группе регистрации Azure AD и заполняет базу данных устройства.

-   Вы разрешаете консоли администрирования Zimperium использовать единый вход (SSO) Azure AD.

-   Вы разрешаете приложению Zimperium выполнять вход в режиме единого входа Azure AD.

## <a name="to-set-up-zimperium-integration"></a>Настройка интеграции Zimperium

1.  Перейдите в [консоль MTD Zimperium](https://staging2-console.zimperium.com) и выполните вход, используя свои учетные данные.

2.  Выберите в левом меню пункт **Управление**.

3.  Перейдите на вкладку **Параметры MDM**.

4.  Выберите **Добавить MDM,** а затем **Microsoft Intune** в списке **поставщиков MDM**.

5.  После установки Microsoft Intune как службы управления мобильными устройствами откроется окно **Настройка Microsoft Intune**. Выберите вариант **Добавить Azure Active Directory** для каждого параметра: **Zimperium zConsole**, **Приложения iOS и Android zIPS**, чтобы разрешить Zimperium взаимодействовать с Intune и Azure AD в режиме единого входа Azure AD.

    > [!IMPORTANT]
    > Чтобы завершить процесс интеграции с Intune, вам потребуется добавить приложения zConsole Zimperium, zIPS iOS и Android.

6.  Нажмите кнопку **Принять**, чтобы разрешить приложению Zimperium взаимодействовать с Intune и Azure Active Directory.

7.  После добавления приложений **Zimperium zConsole** и **iOS и Android zIPS** в Azure AD вам потребуется добавить группы безопасности Azure AD, чтобы служба Zimperium могла синхронизировать группы безопасности Azure AD с собственными компонентами.

8.  Нажмите кнопку **Готово**, чтобы сохранить конфигурацию и запустить первую синхронизацию групп безопасности Azure AD.

## <a name="next-steps"></a>Дальнейшие действия

-   [Настройка приложений Zimperium](mtd-apps-ios-app-configuration-policy-add-assign.md)