---
title: "Управление приложениями iOS, приобретенными по программе Volume Purchase Program | Документация Майкрософт"
titleSuffix: Intune Azure preview
description: "Предварительная версия Intune Azure. Узнайте о том, как синхронизировать приложения, приобретенные по программе Volume Purchase Program в магазине iOS, в Intune, а затем управлять ими и отслеживать их использование."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 3974145b4c244e251ee91a6216a79a6d8b1ad792
ms.contentlocale: ru-ru
ms.lasthandoff: 05/23/2017

---

# <a name="how-to-manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>Управление приложениями iOS, приобретенными по программе корпоративных закупок, с помощью Microsoft Intune


[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Магазин приложений iOS позволяет приобретать сразу несколько лицензий, если приложение планируется использовать в организации. Это позволяет сократить административные расходы на отслеживание нескольких приобретенных копий приложения.

Microsoft Intune помогает управлять приложениями, приобретенными по такой программе, импортируя данные о лицензиях из магазина приложений, отслеживая число используемых лицензий и следя за тем, чтобы число установленных копий приложения не превышало число приобретенных.

Кроме того, можно синхронизировать книги, приобретаемые в магазине Apple VPP Store с помощью Intune, управлять ими и назначать их пользователям. Используйте рабочую нагрузку **Книги** на портале Intune для управления книгами. Процедура управления книгами выглядит так же, как управление приложениями.
Чтобы управлять книгами, отправьте Токен Apple Volume Purchase Program. В настоящее время вы можете назначать книги только как **обязательные** для установки.
Если вы назначаете книгу устройству, на нем должно быть установлено встроенное приложение iBooks. Если это не так, пользователь должен повторно установить приложение, чтобы читать книгу. В настоящее время с помощью Intune нельзя восстановить удаленные встроенные приложения.


## <a name="manage-volume-purchased-apps-for-ios-devices"></a>Управление приложениями для устройств iOS, приобретенными по корпоративной программе
Единовременная покупка нескольких лицензий на приложения iOS осуществляется по программе [Apple Volume Purchase Program для бизнеса](http://www.apple.com/business/vpp/) или [Apple Volume Purchase Program для образовательных учреждений](http://volume.itunes.apple.com/us/store). Для этого необходимо создать учетную запись Apple VPP на веб-сайте Apple и передать токен Apple VPP в Intune.  После этого вы сможете синхронизировать данные корпоративной закупки с Intune и отслеживать использование приобретенных таким образом приложений.

## <a name="before-you-start"></a>Перед началом работы
Для начала вам нужно получить токен Apple VPP и отправить его в Intune. Кроме того, необходимо принять во внимание следующее.

* С учетной записью Intune можно связать несколько токенов программы Volume Purchase Program.
* Если вы уже использовали токен VPP для покупки другого продукта, для использования в Intune создайте новый токен.
* Каждый маркер действителен в течение одного года.
* По умолчанию Intune синхронизируется со службой Apple VPP два раза в день. Синхронизацию вручную можно начать в любое время.
* После импорта токена VPP в Intune не импортируйте его в любые другие решения по управлению устройствами. Это может привести к потере назначенных лицензий и записей пользователей.
* Перед началом использования iOS VPP с Intune удалите все существующие учетные записи пользователей VPP, созданные для других поставщиков управления мобильными устройствами (MDM). Из соображений безопасности Intune не будет синхронизировать эти учетные записи пользователей в Intune. Intune будет синхронизировать данные только из службы Apple VPP, созданной с помощью Intune.
* Intune позволяет добавить до 256 токенов VPP.

## <a name="to-get-and-upload-an-apple-vpp-token"></a>Получение и отправка токена Apple VPP

1. Зарегистрируйтесь на портале Azure.
2. Выберите **Больше служб** > **Другое** > **Intune**.
3. В колонке **Intune** выберите **Мобильные приложения**.
1.  В рабочей нагрузке **Мобильные приложения** выберите **Установка** > **Токены VPP iOS**.
2.  В колонке списка токенов VPP щелкните **Добавить**.
3.  В колонке "Создать токен VPP" укажите перечисленные ниже сведения:
    - **VPP token file** (Файл токена VPP). Зарегистрируйтесь в программе Volume Purchase Program для бизнеса или Volume Purchase Program для образовательных учреждений, если вы еще не сделали этого. После этого скачайте токен Apple VPP для своей учетной записи и выберите его.
    - **Идентификатор Apple ID.** Введите идентификатор Apple ID учетной записи, связанной с программой Volume Purchase Program.
    - **Type of VPP account** (Тип учетной записи VPP). Выберите **Бизнес** или **Образование**.
4. По завершении щелкните **Отправить**.

Токен отобразится в колонке списка токенов.


Данные, хранящиеся в Apple, можно в любое время синхронизировать с Intune, нажав кнопку **Синхронизировать**.

## <a name="to-assign-a-volume-purchased-app"></a>Назначение приложения, приобретенного по программе корпоративных закупок

1. В рабочей нагрузке **Мобильные приложения** выберите **Управление** > **Лицензированные приложения**.
2. В колонке списка приложений выберите приложения, которые нужно назначить, а затем выберите "**...** > **Назначить группы**".
3. В колонке <*имя_приложения*> — **Назначенные группы** выберите **Управление** > **Назначенные группы**.
4. Выберите **Назначить группы**, а затем в колонке **Выбор групп** выберите группы пользователей или устройств Azure AD, которым требуется назначить приложение.
Необходимо выбрать действие назначения **Обязательно**. Кроме того, назначения для групп устройств доступны для новых клиентов, созданных после января 2017 г. Если клиент был создан до этого срока, и нет возможности назначать приложения VPP группам устройств, обратитесь в службу поддержки Intune.
5. По завершении нажмите кнопку **Сохранить**.

Сведения о мониторинге назначений приложений см. в [этой статье](apps-monitor.md).

## <a name="further-information"></a>Дополнительные сведения

При назначении приложения с действием **Обязательная установка** на каждого пользователя, который его устанавливает, расходуется отдельная лицензия.

Чтобы отозвать лицензию, необходимо изменить действие назначения на **Удалить**. После удаления приложения лицензия будет отозвана.

Когда пользователь с соответствующим устройством впервые пытается установить приложение VPP, ему предлагается присоединиться к программе Apple Volume Purchase. Для продолжения установки приложения необходимо принять это предложение.

При назначении приложения VPP как доступного содержимое приложения и лицензия назначаются непосредственно из магазина приложений.
