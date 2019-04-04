---
title: Использовать расширения Mobility Zebra на устройствах Android в Microsoft Intune — Azure | Документация Майкрософт
description: С помощью Microsoft Intune для управления и использования Zebra устройств Android с помощью расширения Mobility Zebra (MX). См. все действия, включая установить приложение корпоративного портала, загрузить неопубликованное приложение, назначить роль администратора устройства, создайте профиль StageNow и многое другое.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: aa2734247569245794bce7fe1de68c8b20c6091f
ms.sourcegitcommit: 44095bbd1502b02201a01604531f4105401fbb92
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58490610"
---
# <a name="use-and-manage-zebra-devices-with-zebra-mobility-extensions-in-microsoft-intune"></a>Использование устройств и управления ими Zebra с расширениями Zebra мобильных устройств в Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune включает в себя широкий набор функций, включая управление приложениями и настройка параметров устройства. Эти встроенные функции и параметры используются для управления устройствами Android, произведенных от Zebra Technologies, также называется «Zebra устройства».

Если вы хотите настроить или добавить дополнительные параметры, относящиеся к Zebra, можно также использовать Zebra **расширения Mobility (MX)** на этих устройствах. 

Данная функция применяется к:

- Android

Ваша компания может использовать Zebra устройств для розничной торговли, на фабриках и многое другое. Например вы занимаетесь розничной торговлей, и среде имеются тысячи Zebra мобильных устройств, используемых торговых партнеров. Intune помогает управлять этими устройствами как часть решения в системе управления мобильными устройствами.

С помощью Intune, вы можете зарегистрировать устройства Zebra для развертывания бизнес приложений на устройствах. «Конфигурация устройства» профили позволяют создавать профили MX для управления параметрами конкретного Zebra.

В этой статье показано, как использовать расширения Mobility Zebra (MX) на устройствах Zebra в Microsoft Intune.

## <a name="before-you-begin"></a>Подготовка к работе

- Убедитесь, что у вас есть последняя версия StageNow классическое приложение от Zebra технологий.
- Не забудьте установить флажок [Zebra полная таблица возможностей MX](http://techdocs.zebra.com/mx/compatibility) (открывается в Zebra веб-сайта) для подтверждения того, профили, создаваемые совместимы с версией MX, версия ОС устройства, а также модели.
- Определенные устройства, таких как устройства TC20/25, поддерживают не все доступные функции MX в StageNow. Не забудьте установить флажок [таблица возможностей в Zebra](http://techdocs.zebra.com/mx/tc2x/) (открывается в Zebra веб-сайта) обновленную поддержку сведения.

## <a name="step-1-install-the-latest-company-portal-app"></a>Шаг 1: Установка последней версии приложения корпоративного портала

На устройстве перейдите в магазин Google Play и загрузить и установить приложение корпоративного портала Intune от корпорации Майкрософт. При установке из Google Play приложение корпоративного портала получает обновления и исправления автоматически.

Если Google Play, скачайте [корпоративного портала Microsoft Intune для Android](https://www.microsoft.com/download/details.aspx?id=49140) (открывается другой веб-сайте Майкрософт), и [неопубликованные его](#sideload-the-company-portal-app) (в этой статье). При установке таким образом, приложение не получает обновления или исправления автоматически. Следует регулярно обновлять и исправление приложения вручную.

### <a name="sideload-the-company-portal-app"></a>Передача данных Корпоративного портала на другое локальное устройство

«Для загрузки неопубликованных приложений» — Если вы не используете Google Play для установки приложения. Чтобы загрузить неопубликованное приложение корпоративного портала используйте StageNow. 

Ниже приведены общие сведения. Конкретные сведения см. в разделе документации по Zebra. [Регистрация в MDM, с помощью StageNow](http://techdocs.zebra.com/stagenow/3-1/Profiles/enrollmdm/) (открывается Zebra на веб-узел) может быть полезным.

1. В StageNow, создайте профиль для **регистрация в MDM**.
2. В **развертывания**, скачайте файл агента управления мобильными Устройствами.
3. Задайте **приложение поддержки** и **загрузить конфигурации** шаги, чтобы **нет**.
4. В **скачать MDM**выберите **перемещение или копирование файла**. Добавьте источник и назначение пакета корпоративного портала Android (APK).
5. В **запуска MDM**, оставьте значения по умолчанию как-является. Добавьте следующие сведения:

    - **Имя пакета**: `com.microsoft.windowsintune.companyportal`
    - **Имя класса**: `com.microsoft.windowsintune.companyportal.views.SplashActivity`

По-прежнему профиль публикации и использовать в приложении StageNow на устройстве. Приложение корпоративного портала устанавливается и открывается на устройстве.

> [!TIP]
> Дополнительные сведения о StageNow и его назначение, см. в разделе [промежуточные устройства StageNow Android](https://www.zebra.com/us/en/products/software/mobile-computers/mobile-app-utilities/stagenow.html) (открывается в Zebra веб-сайта).

## <a name="step-2-confirm-the-company-portal-app-has-device-administrator-role"></a>Шаг 2: Убедитесь, что приложение корпоративного портала с полномочиями администратора устройства

Приложение корпоративного портала требуется администратора устройства для управления устройствами Android. Для активации роли администратора устройства, некоторые устройства Zebra содержит пользовательский интерфейс (UI) на устройстве. Если устройство содержит пользовательский Интерфейс, приложение корпоративного портала предложит пользователю предоставить администратору устройства во время [регистрации](#step-3-enroll-the-device-in-to-intune) (в этой статье).

Если пользовательский Интерфейс не поддерживается, используйте **DevAdmin Manager** в StageNow, чтобы создать профиль, которая вручную предоставляет администратора устройства для приложения корпоративного портала.

Ниже приведены общие сведения. Конкретные сведения см. в разделе документации по Zebra. 
[Установить режим замены батареи как администратор устройства](https://zebratechnologies.force.com/s/article/Set-Battery-Swap-Mode-as-Device-Administrator-using-StageNow-Tool) (открывается веб-сайт Zebra) может быть полезным.

1. В StageNow, создайте профиль и выберите **Xpert режим**.
2. Добавить **DevAdmin Manager** к профилю.
3. Задайте **действие администрирования устройства** для **включить как администратор устройства**.
4. Задайте **пакет имя_устройства** для `com.microsoft.windowsintune.companyportal`.
5. Задайте **имя класса Admin устройства** для `com.microsoft.omadm.client.PolicyManagerReceiver`.

По-прежнему профиль публикации и использовать в приложении StageNow на устройстве. Приложение корпоративного портала предоставляется роль администратора устройства.

## <a name="step-3-enroll-the-device-in-to-intune"></a>Шаг 3: Регистрация устройства в Intune

После выполнения первых двух шагов, приложение корпоративного портала устанавливается на устройстве. Устройство будет готово быть зарегистрированы в Intune.

[Регистрация устройств Android](android-enroll.md) перечислены шаги. Если у вас есть множество устройств Zebra, можно использовать [записи диспетчера регистрации устройств](device-enrollment-manager-enroll.md).

## <a name="step-4-create-a-device-management-profile-in-stagenow"></a>Шаг 4: Создание профиля устройства управления в StageNow

Используйте StageNow для создания профиля, который настраивает параметры, которые вы хотите управлять на устройстве. Конкретные сведения см. в разделе документации по Zebra. [Профили](http://techdocs.zebra.com/stagenow/3-2/stagingprofiles/) (открывается веб-сайт Zebra) может быть полезным.

При создании профиля в StageNow, на последнем шаге выберите **Экспорт в MDM**. Это создает XML-файл. Сохраните этот файл. Он понадобится позже.

> [!TIP]
> Рекомендуется для тестирования профиля, перед развертыванием на устройствах в вашей организации. Чтобы проверить, на последнем шаге при создании профилей с StageNow на компьютере, используйте **тестирования** параметры. Затем использовать созданный StageNow файл с StageNow приложением на устройстве. 
> 
> В приложении StageNow на устройстве отображается журналов, созданных при проверке профиля. [Журналы использования StageNow Zebra устройств Android в Intune](android-zebra-mx-logs-troubleshoot.md) содержит сведения об использовании StageNow журналы для понимания ошибок.

> [!NOTE]
> Если ссылаться на приложения, пакеты обновления или обновлять другие файлы в своем профиле StageNow, нужно предоставить устройству для получения этих обновлений. Чтобы получить обновления, устройство необходимо подключиться к серверу развертывания StageNow при применении профиля. 
> 
> Или можно использовать встроенные функции в Intune для получения этих изменений, включая: 
> - Функции управления приложениями [добавить](apps-add.md), [развертывание](apps-deploy.md), обновить, и [монитор](apps-monitor.md) приложений.
> - Управление [обновлений системы и приложения](device-restrictions-android-for-work.md#device-owner-only) на устройствах под управлением Android для бизнеса

После проверки файла, следующим шагом является развертывание профиля на устройствах с помощью Intune.

> [!NOTE]
> Разверните один профиль для каждого устройства. При наличии нескольких StageNow профили, которые вы хотите развернуть на устройствах, экспорт профилей StageNow и объединить параметры в одном XML-файле, прежде чем добавить его в Intune. 
> 
> Вы не хотите два параметра, которые было настраивать аналогичное свойство в одном файле XML. Целью является избежание конфликтов между параметрами на устройстве.

## <a name="step-5-create-a-profile-in-intune"></a>Шаг 5: Создание профиля в Intune

В Intune создайте профиль конфигурации устройства:

1. На [портале Azure](https://portal.azure.com) выберите **Все службы** > отфильтруйте список по **Intune** > выберите **Intune**.
2. Выберите **Конфигурация устройства** > **Профили** > **Создать профиль**.
3. Укажите следующие свойства.

    - **Имя.** Введите описательное имя для нового профиля.
    - **Описание.** Введите описание профиля. Этот параметр является необязательным, но мы рекомендуем его использовать.
    - **Платформа**. Выберите **Android**.
    - **Тип профиля**: выберите **MX профиля (только Zebra)**.

4. В **MX профиля в формате XML**, добавьте XML-файле профиля [экспортированный из StageNow](#step-4-create-a-device-management-profile-in-stagenow) (в этой статье).
5. Щелкните **OK** > **Создать**, чтобы сохранить изменения. Политика создается и отображается в списке.

Профиль создан, но он пока ничего не делает. Далее [назначьте профиль](device-profile-assign.md) и [отслеживайте его состояние](device-profile-monitor.md).

В следующий раз устройство будет проверять наличие обновлений конфигурации профиля MX развертывается на устройстве. Синхронизировать устройства с помощью Intune, при регистрации устройства, а затем приблизительно каждые 8 часов. Вы также можете [принудительной синхронизации в Intune](device-sync.md). Или на устройстве откройте **приложение корпоративного портала** > **параметры** > **синхронизации**. 

> [!TIP]
> - По соображениям безопасности вы не увидите профиль XML-текст, после его сохранения. Текст зашифрован, и вы увидите только звездочки (`****`). Для справки рекомендуется сохранять копии профили MX, прежде чем добавлять их в Intune.
> 
> - Чтобы обновить профиль, после назначения устройств Zebra, создайте обновленную StageNow XML-файл, изменить существующий профиль Intune и добавьте новый файл StageNow XML. Этот новый файл перезаписывает предыдущей политики StageNow в профиле.

## <a name="next-steps"></a>Дальнейшие шаги

[Назначьте профиль](device-profile-assign.md) и [отслеживайте его состояние](device-profile-monitor.md).

[Использовать StageNow журналы для устранения неполадок устройств Zebra](android-zebra-mx-logs-troubleshoot.md).