---
title: Настройка регистрации в Intune для развертывания гибридных устройств, присоединенных к Active Directory, с помощью Windows Autopilot
titleSuffix: Microsoft Intune
description: Используйте Windows Autopilot для регистрации гибридных устройств, присоединенных к Active Directory, в Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/2/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 77a0c3f3a2e1ed0ee2dbc652049bb7057c736010
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2018
ms.locfileid: "52189968"
---
# <a name="deploy-hybrid-azure-ad-joined-devices-using-intune-and-windows-autopilot-preview"></a>Развертывание гибридных устройств, присоединенных к Azure AD, с помощью Intune и Windows Autopilot (предварительная версия)
С помощью Intune и Windows Autopilot можно настраивать гибридные устройства, присоединенные к Azure Active Directory. Для этого выполните действия, описанные ниже.

> [!NOTE]
> Эта функция станет доступна для пользователей через несколько дней. Вы, возможно, не сможете выполнить эту процедуру, пока функция не будет развернута в вашей учетной записи.

## <a name="prerequisites"></a>Предварительные условия

- Успешно настройте [гибридные устройства, присоединенные к Azure Active Directory](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan).
    - Обязательно [проверьте регистрацию с помощью командлета Get-MsolDevice]( https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-managed-domains#verify-the-registration).

Требования к устройствам:
- Windows 10 с [обновлением за октябрь 2018 г](https://blogs.windows.com/windowsexperience/2018/10/02/how-to-get-the-windows-10-october-2018-update/).
- Доступ к Интернету.
- Доступ к Active Directory (VPN-подключение не поддерживается).
- Пройденный запуск при первом включении компьютера (OOBE).

## <a name="set-up-windows-10-automatic-enrollment"></a>Настройка автоматической регистрации Windows 10

1. Войдите на [портал Azure](https://portal.azure.com) и выберите **Azure Active Directory**.

   ![Снимок экрана портала Azure](./media/auto-enroll-azure-main.png)

2. Выберите **Мобильность (MDM и MAM)**.

   ![Снимок экрана портала Azure](./media/auto-enroll-mdm.png)

3. Выберите **Microsoft Intune**.

   ![Снимок экрана портала Azure](./media/auto-enroll-intune.png)

4. Пользователи, которые развертывают устройства, присоединенные к Azure Active Directory, с помощью Intune и Windows, должны быть членами группы, включенной в вашу **область пользователей MDM**.

   ![Снимок экрана портала Azure](./media/auto-enroll-scope.png)

5. Используйте значения по умолчанию для следующих URL-адресов:
    - **URL-адрес условий использования MDM**;
    - **URL-адрес обнаружения MDM**;
    - **URL-адрес соответствия MDM**.
6. Выберите **Сохранить**.

## <a name="increase-the-computer-account-limit-in-the-organizational-unit"></a>Расширение лимитов учетной записи компьютера в подразделении

Соединитель Intune для Active Directory создает компьютеры, выполняющие регистрацию в Autopilot, в локальном домене Active Directory. Компьютер с соединителем Intune должен иметь права на создание объектов-компьютеров в домене. 

В некоторых доменах компьютеры не имеют прав на создание компьютеров. Или администраторы не хотят расширять лимит учетной записи компьютера в домене. В таких ситуациях можно делегировать права подразделению, в котором создаются гибридные устройства, присоединенные к Azure AD.

Подразделение с правами на создание компьютеров должно соответствовать:
- подразделению, указанному в профиле присоединения к домену;
- или, если профиль не выбран, имени домена компьютера для вашего домена.

1. Откройте **Пользователи и компьютеры Active Directory** (DSA.msc).

2. Щелкните правой кнопкой мыши подразделение, которое будет использоваться для создания гибридных компьютеров, присоединенных к Azure AD > **Делегировать управление**.

    ![Снимок экрана: делегирование управления](media/windows-autopilot-hybrid/delegate-control.png)

3. В мастере **Делегирование управления** выберите **Далее** > **Добавить...**  > **Типы объектов**.

4. В диалоговом окне **Типы объектов** поставьте флажок **Компьютеры** и нажмите **ОК**.

    ![Снимок экрана: делегирование управления](media/windows-autopilot-hybrid/object-types-computers.png)

5. В поле **Введите имена выбираемых объектов** диалогового окна **Выбор пользователей, компьютеров и групп** введите имя компьютера, на котором установлен соединитель.

    ![Снимок экрана: делегирование управления](media/windows-autopilot-hybrid/enter-object-names.png)

6. Выберите **Проверить имена** для проверки записи, а затем нажмите **ОК** > **Далее**.

7. Выберите **Создать особую задачу для делегирования** > **Далее**.

8. Выберите **Только следующие объекты в папке** и отметьте следующие варианты:
    - **Объекты-компьютеры**.
    - **Создать в этой папке выбранные объекты**.
    - **Удалить из этой папки выбранные объекты**.

    ![Снимок экрана: делегирование управления](media/windows-autopilot-hybrid/only-following-objects.png)
    
9. Нажмите кнопку **Далее**.

10. В разделе **Разрешения** поставьте флажок **Полный контроль** (будут отмечены все остальные варианты) > **Далее** > **Готово**.

    ![Снимок экрана: делегирование управления](media/windows-autopilot-hybrid/full-control.png)

## <a name="install-the-intune-connector"></a>Установка соединителя Intune

Соединитель Intune для Active Directory должен быть установлен на компьютере под управлением Windows Server 2016, который имеет доступ к Интернету и Active Directory. Для повышения масштабируемости и доступности или поддержки нескольких доменов Active Directory можно установить несколько соединителей в среде. Мы рекомендуем установить соединитель на сервере, на котором не выполняются другие соединители Intune.

1. Убедитесь, что языковой пакет установлен и настроен, как описано в списке [требований к языкам соединителя Intune (предварительная версия)](https://docs.microsoft.com/windows/deployment/windows-autopilot/intune-connector).
2. В [Intune](https://aka.ms/intuneportal) выберите **Регистрация устройств** > **Регистрация Windows** > **Соединитель Intune для Active Directory (предварительная версия)** > **Добавить соединитель**. 
3. Следуйте инструкциям для загрузки соединителя.
4. Откройте загруженный файл установки соединителя, чтобы установить соединитель (ODJConnectorBootstrapper.exe).
5. В конце установки выберите **Настройка**.
6. Выберите **Вход**.
7. Войдите как глобальный администратор или администратор Intune.
8. Откройте раздел **Регистрация устройств** > **Регистрация Windows** > **Соединитель Intune для Active Directory (предварительная версия)** и убедитесь, что указано состояние подключения **Активно**.

### <a name="configure-web-proxy-settings"></a>Настройка параметров веб-прокси

Если у вас есть веб-прокси в сетевой среде, выполните приведенные здесь инструкции, чтобы соединитель Intune для Active Directory работал правильно: [Работа с имеющимися локальными прокси-серверами](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-configure-connectors-with-proxy-servers).


## <a name="create-a-device-group"></a>Создание группы устройств
1. В [Intune](https://aka.ms/intuneportal) выберите **Группы** > **Создать группу**.
2. В колонке **Группа**
    1. В качестве **Типа группы** выберите **Безопасность**.
    2. Введите **Имя группы** и **Описание группы**.
    3. Выберите **Тип членства**.
3. Если выше вы выбрали **Динамическое устройство** для **Типа членства**, то в колонке **Группа** выберите **Динамические члены устройства**, а в поле **Расширенное правило** введите какой-то из следующих вариантов кода.
    - Если вы хотите создать группу со всеми своими устройствами Autopilot, введите `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`
    - Если вы хотите создать группу со всеми устройствами Autopilot, имеющими определенный ИД заказа, введите `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881") `
    - Если вам нужно создать группу со всеми устройствами Autopilot, имеющими определенный ИД заказа на покупку, введите `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`
    
    Добавив код в **Расширенное правило**, выберите **Сохранить**.
5. Выберите команду **Создать**.  

## <a name="register-your-autopilot-devices"></a>Регистрация устройств Autopilot

Выберите один из следующих способов для регистрации устройств Autopilot.

### <a name="register-autopilot-devices-that-are-already-enrolled"></a>Регистрация уже зарегистрированных устройств Autopilot

1. Создайте профиль развертывания Autopilot и установите для параметра **Преобразовать все целевые устройства в Autopilot** значение **Да**. 
2. Назначьте профиль группе, содержащей элементы, которые вы хотите автоматически зарегистрировать в Autopilot.

Дополнительные сведения см. в разделе [Создание профиля развертывания Autopilot](enrollment-autopilot.md#create-an-autopilot-deployment-profile).

### <a name="register-autopilot-devices-that-arent-enrolled"></a>Регистрация еще не зарегистрированных устройств Autopilot

Если устройства еще не зарегистрированы, вы можете зарегистрировать их самостоятельно. Дополнительные сведения см. в статье [Добавление устройств](enrollment-autopilot.md#add-devices).

### <a name="register-devices-from-an-oem"></a>Регистрация устройств изготовителем

Некоторые изготовители оборудования сами регистрируют устройства. Дополнительные сведения см. на [странице Windows Autopilot](http://aka.ms/WindowsAutopilot).

Когда устройства будут зарегистрированы в Autopilot (и еще не зарегистрированы в Intune), они будут отображаться в трех местах (с серийными номерами в качестве имен):
- Колонка "Устройства Autopilot" в Intune на портале Azure (**Регистрация устройств** > **Регистрация Windows** > **Устройства**).
- Колонка "Устройства Azure AD" в Intune на портале Azure (**Устройства** > **Устройства Azure AD**).
- Колонка "Все устройства AAD" в Azure Active Directory на портале Azure (**Устройства** > **Все устройства**).

После регистрации устройств Autopilot в Intune вы увидите их в четырех местах:
- Колонка "Устройства Autopilot" в Intune на портале Azure (**Регистрация устройств** > **Регистрация Windows** > **Устройства**).
- Колонка "Устройства Azure AD" в Intune на портале Azure (**Устройства** > **Устройства Azure AD**).
- Колонка "Все устройства AAD" в Azure Active Directory на портале Azure (**Устройства** > **Все устройства**).
- Колонка "Все устройства" в Intune на портале Azure (**Устройства** > **Все устройства**).

После регистрации устройств Autopilot их имена изменятся на имя узла устройства. По умолчанию оно начинается с "DESKTOP-".




## <a name="create-and-assign-an-autopilot-deployment-profile"></a>Создание и назначение профиля развертывания AutoPilot
Профили развертывания Autopilot служат для настройки устройств Autopilot.

1. В [Intune](https://aka.ms/intuneportal) последовательно выберите **Регистрация устройства** > **Регистрация Windows** > **Профили развертывания** > **Создать профиль**.
2. Введите **Имя** и, при необходимости, **Описание**.
3. Для параметра **Режим развертывания** выберите **Под управлением пользователя**.
4. В поле **Тип присоединения к Azure AD** выберите **Гибридное присоединение к Azure AD (предварительная версия)**.
5. Выберите **Запуск при первом включении (OOBE)**, настройте параметры и нажмите **Сохранить**.
6. Нажмите **Создать** для создания профиля. 
7. В колонке профиля выберите **Назначения**.
8. Нажмите **Выбрать группы** > в колонке **Выбрать группы** выберите группу устройств > **Выбрать**.

В течение 15 минут состояние профиля устройства изменится с **Не назначено** на **Назначение** и, наконец, **Назначено**.

## <a name="turn-on-the-enrollment-status-page-optional"></a>Включение страницы состояния регистрации (необязательно)

1. В [Intune](https://aka.ms/intuneportal) выберите **Регистрация устройства** > **Регистрация Windows** > **Enrollment Status Page (Preview)** (Страница состояния регистрации, предварительная версия).
2. В колонке **Enrollment Status Page** (Страница состояния регистрации) выберите **По умолчанию** > **Параметры**.
3. Для параметра **Show app and profile installation progress** (Показать ход установки приложений и профилей) выберите значение **Да**.
4. При необходимости настройте остальные параметры.
5. Выберите **Сохранить**.

## <a name="create-and-assign-a-domain-join-profile"></a>Создание и назначение профиля присоединения к домену

1. В [Intune](https://aka.ms/intuneportal) выберите **Конфигурация устройства** > **Профили** > **Создать профиль**.
2. Укажите следующие свойства.
   - **Имя.** Введите описательное имя для нового профиля.
   - **Описание.** Введите описание профиля.
   - **Платформа**: выберите **Windows 10 и более поздняя версия**.
   - **Тип профиля**: выберите **Присоединение к домену (предварительная версия)**.
3. Выберите **Параметры** и укажите **Префикс имени компьютера**, **Доменное имя** и **Подразделение** (необязательно). 
4. Нажмите кнопки **ОК**  >  **Создать**. Созданный профиль отобразится в списке.
5. Чтобы назначить профиль, следуйте инструкциям в разделе [Назначение профиля устройства](device-profile-assign.md#assign-a-device-profile). 

## <a name="next-steps"></a>Дальнейшие шаги

После настройки Windows Autopilot узнайте, как управлять этими устройствами. Дополнительные сведения см. в разделе [Что такое управление устройствами с помощью Microsoft Intune](device-management.md)?