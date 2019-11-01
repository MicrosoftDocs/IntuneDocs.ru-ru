---
title: Интерактивный сценарий. Развертывание Microsoft Edge для мобильных устройств
titleSuffix: Microsoft Intune
description: Ознакомьтесь с интерактивным сценарием развертывания Microsoft Edge для мобильных устройств с портала управления устройствами Microsoft 365.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e86f3a469169e7a805cb3f56e570ba4d3a90e925
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585700"
---
# <a name="guided-scenario---deploy-microsoft-edge-for-mobile"></a>Интерактивный сценарий. Развертывание Microsoft Edge для мобильных устройств 

Следуя этому [интерактивному сценарию](~/fundamentals/guided-scenarios-overview.md), вы можете назначить приложение Microsoft Edge пользователям устройств с iOS или Android в вашей организации. Назначение этого приложения позволит пользователям без труда просматривать содержимое с помощью корпоративных устройств. 

Microsoft Edge позволяет пользователям избавиться от переизбытка информации с помощью встроенных функций, которые помогают им консолидировать и упорядочивать рабочее содержимое, а также управлять им. Пользователи устройств с iOS и Android, входящие в Microsoft Edge по корпоративным учетным записям Azure AD, найдут в браузере заполненную рабочую область **Избранное** и фильтры веб-сайтов, которые вы определите.

> [!NOTE]
> Если вы запретили пользователям регистрировать устройства с iOS или Android, в этом сценарии не будет включена регистрация и пользователям придется установить Edge самостоятельно.
Политики Intune поддерживают следующие корпоративные функции Microsoft Edge: 

- **Двойное удостоверение** — пользователи могут добавлять для просмотра как рабочую учетную запись, так и личную. Реализовано полное разделение между двумя удостоверениями, как и в архитектуре для Office 365 и Outlook. Администраторы Intune смогут задать необходимые политики для защищенного просмотра в браузере в рабочей учетной записи. 
- **Интеграция политики защиты приложений Intune** — администраторы теперь могут применять политики защиты приложений для Microsoft Edge, включая контроль вырезания, копирования и вставки, предотвращая создания снимков экрана и гарантируя, что выбранные пользователем ссылки открываются исключительно в других управляемых приложениях.
- **Интеграция с прокси-сервером приложений Azure** — администраторы могут управлять доступом к приложениям и веб-приложениям SaaS, обеспечивая запуск браузерных приложений только в защищенном браузере Microsoft Edge, независимо от того, подключаются ли пользователи из корпоративной сети или через Интернет. 
- **Ярлыки для управляемого избранного и домашней страницы** — для более удобного доступа администраторы могут настроить отображение URL-адресов в разделе избранного при работе пользователей в корпоративном контексте. Администраторы могут задать ярлык домашней страницы, который будет отображаться первым при открытии корпоративным пользователем новой страницы или вкладки в Microsoft Edge.

## <a name="prerequisites"></a>Предварительные условия

- [Задание Intune в качестве центра управления мобильными устройствами](mdm-authority-set.md#set-mdm-authority-to-intune). Параметр центра управления мобильными устройствами (MDM) определяет способ администрирования устройств. ИТ-администратор должен задать центр MDM, чтобы пользователи могли регистрировать устройства для управления.
- Требуются разрешения администратора Intune:
    - Управляемые приложения: чтение, создание, удаление и назначение
    - Мобильные приложения: чтение, создание и назначение
    - Наборы политик: чтение, создание и назначение
    - Организация: чтение, изменение

## <a name="step-1---introduction"></a>Шаг 1. Введение

Следуя указаниям в статье **Развертывание Microsoft Edge для мобильных устройств**, вы настроите базовое развертывание Microsoft Edge для выбранной группы пользователей iOS и Android. В этом развертывании будет реализована **поддержка двойной идентификации**, а также **управляемый раздел "Избранное" и ярлыки начальной страницы**. Кроме того, на устройствах, зарегистрированных выбранными пользователями, служба Intune будет автоматически устанавливать приложение Microsoft Edge. Такая автоматическая установка будет выполняться для всех типов регистрации, управляемых пользователем, в том числе: 
- Регистрация устройств с iOS с помощью приложения корпоративного портала 
- Регистрация соответствия пользователей iOS с помощью Apple Business Manager 
- Регистрация устройств с Android прежних версий с помощью приложения корпоративного портала 

В этом интерактивном сценарии **MyApps** будут автоматически отображаться в избранном Microsoft Edge, а сам браузер будет настроен с той же фирменной символикой, что и приложение корпоративного портала Intune. 

### <a name="what-you-will-need-to-continue"></a>Что потребуется для продолжения
Мы запросим сведения об избранном на рабочем месте и фильтрах, необходимых для веб-страниц. Прежде чем продолжить, необходимо выполнить следующие задачи.

- Добавьте пользователей в группы Azure AD. Дополнительные сведения см. в разделе [Создание базовой группы и добавление членов с помощью Azure Active Directory](https://go.microsoft.com/fwlink/?linkid=2102458).
- Зарегистрируйте устройства с iOS и Android в Intune. Дополнительные сведения см. в статье [Регистрация устройств](https://go.microsoft.com/fwlink/?linkid=2102547).
- Соберите список избранного для рабочего места для добавления в Microsoft Edge.
- Соберите список фильтров веб-сайтов для применения в Microsoft Edge.

## <a name="step-2---basics"></a>Шаг 2. Основные сведения

На этом шаге необходимо ввести имя и описание новых политик Microsoft Edge. К этим политикам можно обращаться позже, если необходимо изменить назначения и конфигурации. В интерактивном сценарии приложение Microsoft Edge для iOS будет добавлено и назначено для устройств с iOS, а Microsoft Edge для Android будет добавлено и назначено для устройств с Android. Кроме того, на этом шаге будут созданы политики конфигурации для этих приложений.

## <a name="step-3---configuration"></a>Шаг 3. Настройка

На этом шаге в интерактивном сценарии Microsoft Edge будет настраиваться для отображения всех других приложений, назначенных пользователям через Intune, и использования той же фирменной символики, что и в приложении корпоративного портала Microsoft Intune. Вы можете дополнительно настроить Microsoft Edge, указав **URL-адрес ярлыка начальной страницы**, **список управляемых закладок** и список **заблокированных URL-адресов**. **URL-адрес ярлыка начальной страницы** будет отображаться как первый значок под строкой поиска при открытии новой вкладки в Microsoft Edge на устройстве. **Управляемые закладки** представляют собой список избранных URL-адресов, доступных пользователям при использовании Microsoft Edge в своем рабочем контексте. **Заблокированные URL-адреса** указывают сайты, заблокированные для пользователей в рабочем контексте. Все остальные сайты будут разрешены. 

## <a name="step-4---assignments"></a>Шаг 4. Назначения

На этом шаге можно выбрать группы пользователей, которым вы хотите предоставить возможность работы с Microsoft Edge для мобильных устройств. Приложение Microsoft Edge также будет установлено на всех устройствах с iOS и Android, зарегистрированных этими пользователями.

## <a name="step-5---review--create"></a>Шаг 5. Проверка и создание

На последнем шаге вы можете ознакомиться с краткими сведениями о настроенных параметрах. После просмотра настроек нажмите кнопку **Создать**, чтобы завершить интерактивный сценарий. 

> [!NOTE]
> На настройку Edge может уйти до 12 часов. Дополнительные сведения см. в статье [Политики конфигурации приложений для Microsoft Intune](~/apps/app-configuration-policies-overview.md).

> [!IMPORTANT]
> После завершения интерактивного сценария отобразится сводка. Ресурсы, перечисленные в сводке, можно изменить позже, однако таблица, в которой они отображаются, не будет сохранена.

## <a name="next-steps"></a>Дальнейшие шаги

- Повысьте безопасность использования Microsoft Edge, настроив интеграцию политики защиты приложений Intune. Дополнительные сведения см. в статье [Политики защиты приложений для Microsoft Edge](~/apps/manage-microsoft-edge.md#application-protection-policies-for-microsoft-edge).
- Если у вас есть сайты интрасети, которые вы хотите включить, познакомьтесь с защитой доступа с помощью интеграции с прокси-сервером приложений Azure. Дополнительные сведения см. в разделе [Настройка параметров Application Proxy для Microsoft Edge](~/apps/manage-microsoft-edge.md#configure-application-proxy-settings-for-microsoft-edge).
