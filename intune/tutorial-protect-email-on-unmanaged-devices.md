---
title: Руководство. Защита электронной почты Exchange Online на неуправляемых устройствах
titlesuffix: Microsoft Intune
description: Сведения о том, как защитить Office 365 Exchange Online с помощью политик защиты приложений Intune и условного доступа Azure AD.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 12/11/2018
ms.topic: tutorial
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8339f91468abca548b3923df4d4380aabb88c5a8
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/07/2019
ms.locfileid: "55848718"
---
# <a name="tutorial-protect-exchange-online-email-on-unmanaged-devices"></a>Руководство. Защита электронной почты Exchange Online на неуправляемых устройствах

Здесь вы узнаете, как использовать политики защиты приложений с условным доступом для защиты Exchange Online, даже когда устройства не зарегистрированы в решении для управления устройствами, таком как Intune. Из этого руководства вы узнаете, как выполнять следующие задачи: 

> [!div class="checklist"]
> * Создавать политику защиты приложений Intune для приложения Outlook. Вы ограничите операции пользователей с данными, запретив команду "Сохранить как" и ограничив действия вырезания, копирования и вставки. 
> * Создавать политики условного доступа Azure Active Directory (Azure AD), которые позволяют получать доступ к электронной почте компании в Exchange Online только из приложения Outlook. Вы также настроите требование многофакторной проверки подлинности (MFA) для клиентов c современной проверкой подлинности, таких как Outlook для iOS и для Android.

## <a name="prerequisites"></a>Предварительные условия
  - Для работы с этим руководством вам потребуется тестовый клиент со следующими подписками:
    - Azure Active Directory Premium ([бесплатная пробная версия](https://azure.microsoft.com/free/?WT.mc_id=A261C142F));
    - подписка Intune ([бесплатная пробная версия](free-trial-sign-up.md));
    - Office 365 бизнес, которая включает Exchange ([бесплатная пробная версия](https://go.microsoft.com/fwlink/p/?LinkID=510938)).

## <a name="sign-in-to-intune"></a>Вход в Intune

Войдите в [Intune](https://aka.ms/intuneportal) в качестве глобального администратора или администратора службы Intune. Чтобы найти Intune, на портале Azure выберите **Все службы**  >  **Intune**.

## <a name="create-the-app-protection-policy"></a>Создание политики защиты приложений
В этом руководстве мы настроим политику защиты приложений Intune для приложения Outlook, чтобы обеспечить защиту на уровне приложения. Мы настроим требование ввода ПИН-кода для открытия приложения в рабочем контексте, а также ограничим обмен данными между приложениями и предотвратим сохранение корпоративных данных в личных расположениях.

1.  В Intune выберите **Клиентские приложения** > **Политики защиты приложений** > **Добавить политику**.
2.  В поле **Имя** введите **Тестирование политики приложения Outlook**.
3.  В поле **Описание** введите **Тестирование политики приложения Outlook**.
4.  Выберите **Приложения**. В списке приложений выберите **Outlook**, а затем щелкните **Выбрать**.
5.  Выберите **Параметры**. 
6.  В разделе **Перемещение данных** выберите следующие параметры.

    - Для поля **Разрешить приложению передавать данные другим приложениям** выберите **Нет**.
    - Для поля **Разрешить приложению принимать данные от других приложений** установите значение **Нет**.
    - В поле **Запретить "Сохранить как"** выберите **Да**.
    - Для поля **Ограничить операции "вырезать", "копировать" и "вставить" с другими приложениями** задайте значение **Заблокировано**.
   
     ![Выбор параметров перемещения данных для политики защиты приложений Outlook](media/tutorial-protect-email-on-unmanaged-devices/outlook-app-data-relocation.png)
    
7.  В разделе **Действия доступа** выберите следующие параметры.

    - В поле **Требовать ПИН-код для доступа** установите значение **Да**.
    - Для поля **Требовать для доступа учетные данные организации** выберите **Да**.
    - Для всех других параметров оставьте значения по умолчанию.
 
     ![Выбор действий доступа политики защиты приложений Outlook](media/tutorial-protect-email-on-unmanaged-devices/outlook-app-access-actions.png)

9.  Нажмите кнопку **ОК**.
10. Выберите **Создать**.

Политика защиты приложений для Outlook создана. Теперь можно настроить условный доступ, чтобы требовать от различных устройств использовать приложение Outlook.

## <a name="create-conditional-access-policies"></a>Создание политик условного доступа
Теперь мы создадим две политики условного доступа, чтобы охватить все платформы устройств. Первая политика будет требовать, чтобы клиенты с современной проверкой подлинности, например Outlook для iOS и Outlook для Android, использовали MFA и утвержденное приложение Outlook. Вторая — чтобы клиент Exchange ActiveSync использовал утвержденное приложение Outlook. (В настоящее время Exchange Active Sync не поддерживает условия, отличные от условий платформы устройства.) Политики условного доступа можно настроить на портале Azure AD или Intune. Мы уже вошли на портал Intune, так что давайте создадим политику здесь.
### <a name="create-an-mfa-policy-for-modern-authentication-clients"></a>Создание политики требования многофакторной проверки подлинности для клиентов с современной проверкой подлинности
1.  В Intune последовательно выберите **Условный доступ** > **Политики** > **Новая политика**.
1.  В поле **Имя** введите **Тестовая политика для клиентов с современной проверкой подлинности**. 
3.  В разделе **Назначения** выберите **Пользователи и группы**. Откройте вкладку **Включить** и выберите **Все пользователи**, затем щелкните **Готово**.

4.  В разделе **Назначения** выберите **Облачные приложения**. Так как нам нужна защита для электронной почты Office 365 Exchange Online, выполните следующие инструкции:
     
    1. На вкладке **Включить** выберите **Выбрать приложения**.
    2. Щелкните **Выбрать**. 
    3. В списке приложений выберите **Office 365 Exchange Online**, а затем щелкните **Выбрать**. 
    4. Нажмите кнопку **Готово**.
  
    ![Выбор приложения Office 365 Exchange Online](media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-cloud-apps.png)

5.  В разделе **Назначения** выберите **Условия** > **Платформы устройств**.
     
    1. В разделе **Настройка** выберите **Да**.
    2. На вкладке **Включить** выберите **All platforms (including unsupported)** (Все платформы (в том числе и неподдерживаемые)). 
    3. Нажмите кнопку **Готово**.
   
6.  На панели **Условия** выберите **Клиентские приложения**.
     
    1. В разделе **Настройка** выберите **Да**.
    2. Выберите **Мобильные приложения и настольные клиенты** и **Клиенты с современной проверкой подлинности**.
    3. Снимите остальные флажки.
    4. Выберите **Готово** и еще раз щелкните **Готово**.
    
    ![Выбор приложения Office 365 Exchange Online](media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-client-apps.png)

7.  В разделе **Элементы управления доступом** выберите **Предоставить**. 
     
    1. На панели **Предоставить** выберите **Предоставить доступ**.
    2. Затем выберите **Требовать многофакторную проверку подлинности**.
    4. Выберите **Require approved client app** (Требовать утвержденное клиентское приложение).
    5. В разделе **Для нескольких элементов управления** выберите **Требовать все выбранные элементы управления**. Этот параметр гарантирует, что, когда устройство обратится к электронной почте, будут применяться оба выбранных требования.
    6. Щелкните **Выбрать**.
     
    ![Выбор приложения Office 365 Exchange Online](media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-mfa.png)

8.  В разделе **Включить политику** выберите **Вкл.**
     
    ![Выбор приложения Office 365 Exchange Online](media/tutorial-protect-email-on-unmanaged-devices/enable-policy.png)

9.  Выберите **Создать**.

Политика условного доступа для клиентов с современной проверкой подлинности создана. Теперь можно создать политику для клиентов Exchange Active Sync.

### <a name="create-a-policy-for-exchange-active-sync-clients"></a>Создание политики для клиентов Exchange Active Sync
1.  В Intune последовательно выберите **Условный доступ** > **Политики** > **Новая политика**.
2.  В поле **Имя** введите **Тестовая политика для клиентов EAS**. 
3.  В разделе **Назначения** выберите **Пользователи и группы**. Откройте вкладку **Включить** и выберите **Все пользователи**, затем щелкните **Готово**.

4.  В разделе **Назначения** выберите **Облачные приложения**. Выберите электронную почту Office 365 Exchange Online, выполнив следующие действия.
     
    1. На вкладке **Включить** выберите **Выбрать приложения**.
    2. Щелкните **Выбрать**. 
    3. В списке приложений выберите **Office 365 Exchange Online**, а затем щелкните **Выбрать**. 
    4. Нажмите кнопку **Готово**.

5.  В разделе **Назначения** выберите **Условия** > **Платформы устройств**.
     
    1. В разделе **Настройка** выберите **Да**.
    2. На вкладке **Включить** выберите **Все платформы (в том числе и неподдерживаемые)**, а затем щелкните **Готово**. 
    3. Еще раз щелкните **Готово**.

6.  На панели **Условия** выберите **Клиентские приложения**.
     
    1. В разделе **Настройка** выберите **Да**.
    2. Щелкните **Мобильные приложения и настольные клиенты**.
    3. Выберите **Клиенты Exchange ActiveSync** и **Применить политику только к поддерживаемым платформам**. 
    4. Снимите все остальные флажки.
    5. Выберите **Готово** и еще раз щелкните **Готово**.
    
    ![Выбор приложения Office 365 Exchange Online](media/tutorial-protect-email-on-unmanaged-devices/eas-client-apps.png)

7.  В разделе **Элементы управления доступом** выберите **Предоставить**. 
     
    1. На панели **Предоставить** выберите **Предоставить доступ**.
    4. Выберите **Require approved client app** (Требовать утвержденное клиентское приложение). Снимите все остальные флажки.
    6. Щелкните **Выбрать**.
     
    ![Выбор приложения Office 365 Exchange Online](media/tutorial-protect-email-on-unmanaged-devices/eas-grant-access.png)

8.  В разделе **Включить политику** выберите **Вкл.**

9.  Выберите **Создать**.

Теперь политики защиты приложений и условного доступа настроены и готовы для тестирования. 

## <a name="try-it-out"></a>Попробуйте!
Если применяются созданные здесь политики, для доступа к электронной почте Office 365 нужно будет зарегистрировать устройства в Intune и использовать мобильное приложение Outlook. Чтобы проверить этот сценарий на устройстве iOS, попробуйте войти в Exchange Online с учетными данными любого пользователя из тестового клиента.
1. Чтобы протестировать политики на iPhone, последовательно выберите **Параметры** > **Passwords & Accounts (Пароли и учетные записи)** > **Добавить учетную запись** > **Exchange**.
2. Введите адрес электронной почты, назначенный для пользователя в тестовом клиенте, и щелкните **Далее**.
3. Выберите **Вход**.
4. Введите пароль тестового пользователя и щелкните **Войти**.
5. Отображается сообщение **More information is required** (Требуется больше информации). Это означает, что вам предлагается настроить многофакторную проверку подлинности. Настройте этот дополнительный метод проверки.
6. Далее вы увидите сообщение о том, что вы пытаетесь открыть этот ресурс с помощью приложения, не утвержденного вашим ИТ-отделом. Это означает, что использование встроенного почтового приложения для вас недоступно. Отмените вход.
7.  Откройте приложение Outlook и выберите **Параметры** > **Добавить учетную запись** > **Добавить учетную запись электронной почты**.
8. Введите адрес электронной почты, назначенный для пользователя в тестовом клиенте, и щелкните **Далее**.
9. Щелкните **Sign in with Office 365** (Войти с помощью Office 365). Вам будут предложены дополнительная проверка подлинности и регистрация. После входа вы можете протестировать операции, такие как "вырезать", "копировать", "вставить" и "Сохранить как".

## <a name="clean-up-resources"></a>Очистка ресурсов
Если тестовые политики больше не нужны, их можно удалить.
1. Войдите в [Intune](https://aka.ms/intuneportal) в качестве глобального администратора или администратора службы Intune.
2. Последовательно выберите **Соответствие устройства** > **Политики**.
3. В списке **Имя политики** откройте контекстное меню (**...**) для тестовой политики, а затем щелкните **Удалить**. Для подтверждения щелкните **ОК**.
4. Последовательно выберите **Условный доступ** > **Политики**.
5. В списке **Имя политики** для каждой тестовой политики откройте контекстное меню (**...**), а затем щелкните **Удалить**. Нажмите кнопку **Да** для подтверждения.

 ## <a name="next-steps"></a>Дальнейшие шаги 
В этом руководстве вы создали политики защиты приложений, чтобы ограничить действия пользователей в приложении Outlook, а также политики условного доступа, чтобы требовать использование приложения Outlook и многофакторной проверки подлинности на клиентах с современной проверкой подлинности. Дополнительные сведения об использовании Intune с условным доступом для защиты других приложений и служб см. в статье о [настройке условного доступа](conditional-access.md).