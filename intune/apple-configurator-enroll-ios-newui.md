---
title: "Регистрация устройств iOS с использованием Apple Configurator и помощника по настройке"
titlesuffix: Azure portal
description: "Узнайте, как зарегистрировать корпоративные устройства iOS с использованием Apple Configurator и помощника по настройке (новый пользовательский интерфейс)."
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/08/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 671e4d76-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 186b021079224260e9ffe0f5c2c5a38f513c9f33
ms.sourcegitcommit: 9bd6278d129fa29f184b2d850138f8f65f3674ea
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="enroll-ios-devices-with-apple-configurator"></a>Регистрация устройств iOS с помощью Apple Configurator

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

> [!NOTE]
> ### <a name="temporary-user-interface-differences"></a>Временные отличия в пользовательском интерфейсе
>
>Пользовательские интерфейсы для функций, описанных на этой странице, находятся в процессе обновления. Эти обновления будут развернуты во всех учетных записях до конца апреля.
>
>Если страница **регистрации устройств** выглядит как на следующем рисунке, значит пользовательский интерфейс обновлен и вы можете использовать эту страницу справки.
>
>![Новый пользовательский интерфейс](./media/appleenroll-newui.png)
>
>Если же страница **регистрации устройств** выглядит как на следующем рисунке, то пользовательский интерфейс еще не обновлен для вашей учетной записи. Перейдите на [эту страницу справки](apple-configurator-enroll-ios.md).
>
>![Старый пользовательский интерфейс](./media/appleenroll-oldui.png)

Intune поддерживает регистрацию устройств iOS с помощью средства [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344), запущенного на компьютере Mac. Для регистрации с помощью Apple требуется USB-подключение каждого устройства iOS компьютеру Mac для настройки корпоративной регистрации. Зарегистрировать устройства в Intune с помощью Apple Configurator можно двумя способами:
- **Регистрация с использованием помощника по настройке**. Выполняет сброс устройства к заводским настройкам и подготавливает его для регистрации с использованием помощника по настройке.
- **Прямая регистрация**. Этот процесс не выполняет сброс устройства к заводским настройкам. Он регистрирует устройство, используя параметры iOS. Этот способ предназначен только для устройств **без сходства пользователей**.

Методы регистрации Apple Configurator нельзя использовать с [диспетчером регистрации устройств](device-enrollment-manager-enroll.md).

## <a name="prerequisites"></a>Предварительные условия

- Физический доступ к устройствам iOS
- [Настройка центра MDM](mdm-authority-set.md)
- [Сертификат Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)
- Серийные номера устройств (только для регистрации с использованием помощника по настройке)
- Соединительные USB-кабели
- Компьютер с macOS и запущенным средством [Apple Configurator 2.0](https://itunes.apple.com/app/apple-configurator-2/id1037126344)

## <a name="create-an-apple-configurator-profile-for-devices"></a>Создание профиля Apple Configurator для устройств

Профиль регистрации устройств задает параметры, применяемые во время регистрации. Эти параметры применяются только один раз. Выполните следующие действия, чтобы создать профиль регистрации для регистрации устройств iOS с использованием Apple Configurator.

1. В [Intune](https://aka.ms/intuneportal) выберите **Регистрация устройства** > **Регистрация Apple** > **Apple Configurator** > **Профили** > **Создать**.

    ![Создание профиля для Apple Configurator](./media/apple-configurator-enroll-ios/apple-config-create-profile.png)

2. В разделе **Создание профиля регистрации** введите **имя** и **описание** профиля для использования в административных целях. Пользователям эти сведения не отображаются. Поле "Имя" можно использовать для создания динамической группы в Azure Active Directory. Используйте имя профиля для определения параметра enrollmentProfileName, чтобы назначать устройства с этим профилем регистрации. Узнайте больше о динамических группах Azure Active Directory.

    ![Снимок экрана создания профиля с выбранным параметром регистрации со сходством пользователей.](./media/apple-configurator-profile-create.png)

3. В поле **Сходство пользователей** укажите, должны ли устройства с этим профилем регистрироваться с назначенным пользователем или без него.

    - **Регистрация со сходством пользователей** — выберите этот вариант для устройств, которые принадлежат пользователям и которые должны использовать корпоративный портал для выполнения таких действий, как установка приложений. Устройство должно быть связано с пользователем с помощью помощника по настройке, после чего оно может получить доступ к корпоративным данным и электронной почте. Поддерживается только при регистрации с использованием помощника по настройке. Для сходства пользователей требуется [конечная точка WS-Trust 1.3 в режиме "Имя пользователя/смешанный"](https://technet.microsoft.com/library/adfs2-help-endpoints). [Дополнительные сведения](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

   > [!NOTE]
   > Многофакторная идентификация (MFA) не работает во время регистрации со сходством пользователей. После регистрации MFA работает на этих устройствах должным образом. Устройства не могут предложить изменить пароль пользователям при первом входе. Кроме того, пользователям, срок действия паролей которых истек, не будет предложено сбросить пароль во время регистрации. Им потребуется сбросить пароль с другого устройства.

    - **Регистрация без сходства пользователей** — выберите этот вариант для устройств, не связанных с одним пользователем. Используйте этот вариант для устройств, которые выполняют задачи без осуществления доступа к локальным данным пользователя. Приложения, для которых необходимо связывание с пользователем (включая приложение корпоративного портала, используемое для установки бизнес-приложений), не будут работать. Требуется для прямой регистрации.

4. Если выбран вариант **Регистрация со сходством пользователей**, вы можете разрешить пользователям выполнять аутентификацию с помощью корпоративного портала, а не помощника по настройке Apple.

6. Выберите **Создать**, чтобы сохранить профиль.

## <a name="setup-assistant-enrollment"></a>Регистрация с использованием помощника по настройке

### <a name="add-apple-configurator-serial-numbers"></a>Добавление серийных номеров Apple Configurator

1. Создайте список значений с разделителями-запятыми (CSV-файл) с двумя столбцами без заголовка. Добавьте серийный номер в левый столбец, а сведения — в правый. Текущая максимальная длина списка составляет 5000 строк. В текстовом редакторе список CSV-файлов выглядит примерно так:

    F7TLWCLBX196, сведения об устройстве</br>
    DLXQPCWVGHMJ, сведения об устройстве

   Узнайте, [как найти серийный номер устройства iOS](https://support.apple.com/HT204073).
2. В [Intune](https://aka.ms/intuneportal) выберите **Регистрация устройства** > **Регистрация Apple** > **Apple Configurator** > **Устройства** > **Добавить**.

5. Выберите **Профиль регистрации**, к которому применяются импортируемые серийные номера. Чтобы существующие данные о серийном номере перезаписать новыми данными, установите флажок **Перезапись сведений для существующих идентификаторов**.
6. В разделе **Импортировать устройства** перейдите к CSV-файлу с серийными номерами и выберите **Добавить**.

### <a name="reassign-a-profile-to-device-serial-numbers"></a>Переназначение профиля серийным номерам устройств

Назначить профиль регистрации можно при импорте серийных номеров iOS для регистрации Apple Configurator. Профили также можно назначать на портале Azure:
- **Устройства Apple Configurator**
- **Профили AC**

#### <a name="assign-from-apple-configurator-devices"></a>Назначение из устройств Apple Configurator
1. В [Intune](https://aka.ms/intuneportal) выберите **Регистрация устройства** > **Регистрация Apple** > **Apple Configurator** > **Устройства** > выберите серийные номера > **Назначить профиль**.
2. В разделе **Назначить профиль** выберите **новый профиль**, который следует назначить, а затем щелкните **Назначить**.

#### <a name="assign-from-profiles"></a>Назначение из профилей
1. В [Intune](https://aka.ms/intuneportal) выберите **Регистрация устройства** > **Регистрация Apple** > **Apple Configurator** > **Профили** > выберите профиль.
2. В профиле выберите **Назначенные устройства**, а затем щелкните **Назначить**.
3. Выполните фильтрацию для поиска серийных номеров устройств, которые необходимо назначить профилю, выберите устройства, а затем щелкните **Назначить**.

### <a name="export-the-profile"></a>Экспорт профиля
После создания профиля и назначения серийных номеров необходимо экспортировать профиль из Intune в виде URL-адреса. Затем он импортируется в Apple Configurator на компьютер Mac для развертывания на устройствах.

1. В [Intune](https://aka.ms/intuneportal) выберите **Регистрация устройства** > **Регистрация Apple** > **Apple Configurator** > **Профили** > выберите профиль для экспорта.
2. В профиле выберите **Экспорт профиля**.
3. Скопируйте **URL-адрес профиля**. Позже его можно добавить в Apple Configurator для определения профиля Intune, используемого устройствами iOS.

  Затем этот профиль импортируется в Apple Configurator в следующей процедуре для определения профиля Intune, используемого устройствами iOS.

### <a name="enroll-devices-with-setup-assistant"></a>Регистрация устройств с использованием помощника по настройке

1. На компьютере Mac откройте **Apple Configurator 2**. В строке меню щелкните **Apple Configurator 2** и выберите **Preferences** (Предпочтения).
    > [!WARNING]
    > Во время процесса регистрации настройки устройств сбрасываются до заводских. Рекомендуется выполнить сброс устройства и включить питание. При подключении на устройстве должен отображаться экран **приветствия**.

2. На панели **предпочтений** выберите **Серверы** и щелкните значок "+", чтобы запустить мастер сервера MDM. Нажмите кнопку **Далее**.
3. Введите **имя узла или URL-адрес** и **URL-адрес регистрации** сервера MDM в разделе "Регистрация помощника по установке" для устройств iOS с Microsoft Intune. В поле "URL-адрес регистрации" введите URL-адрес профиля регистрации, экспортированный из Intune. Нажмите кнопку **Далее**.  
    Предупреждением "server URL is not verified" (URL-адрес сервера не проверен) можно пренебречь. Чтобы продолжить, нажимайте кнопку **Далее** до завершения работы мастера.
4.  Подключите мобильные устройства iOS к компьютеру Mac с помощью USB-адаптера.
5.  Выберите устройства iOS, которыми необходимо управлять, а затем щелкните **Подготовить**. На панели **Prepare iOS Device** (Подготовка устройства iOS) выберите **Manual** (Вручную) и нажмите кнопку **Next** (Далее).
6. На панели **Enroll in MDM Server** (Регистрация на сервере MDM) выберите имя созданного вами сервера и нажмите кнопку **Далее**.
7. На панели **Supervise Devices** (Контроль за устройствами) выберите уровень контроля и нажмите кнопку **Next** (Далее).
8. На панели **Create an Organization** (Создание организации) выберите **Организация** или создайте организацию, а затем нажмите кнопку **Далее**.
9. На панели **Configure iOS Setup Assistant** (Настройка помощника по настройке iOS) выберите действия, которые будут отображаться для пользователя, и нажмите кнопку **Подготовить**. При появлении запроса пройдите проверку подлинности, чтобы обновить параметры отношения доверия.  
10. После завершения подготовки устройства iOS отключите кабель USB.  

### <a name="distribute-devices"></a>Распределение устройств
Теперь устройства готовы к регистрации в корпоративной среде. Выключите устройства и распределите их пользователям. Когда пользователи включат свои устройства, запустится помощник по настройке.

После получения устройств пользователи должны выполнить действия в помощнике по настройке. Устройства, для которых настроено сходство пользователей, могут установить и запустить приложение корпоративного портала для скачивания приложений и управления устройствами.

## <a name="direct-enrollment"></a>Прямая регистрация
Для выполнения прямой регистрации устройств iOS с помощью Apple Configurator не требуется серийный номер устройства. Кроме того, в целях идентификации можно указать имя устройства, которое будет использоваться Intune во время регистрации. Приложение корпоративного портала не поддерживается для устройств с прямой регистрацией. Для этого сброс параметров на устройстве не требуется.

Приложения, для которых необходимо взаимодействие с пользователем (включая приложение корпоративного портала, используемое для установки бизнес-приложений), нельзя установить.

### <a name="export-the-profile-as-mobileconfig-to-ios-devices"></a>Экспорт профиля в качестве MOBILECONFIG-файла на устройства iOS

1. В [Intune](https://aka.ms/intuneportal) выберите **Регистрация устройства** > **Регистрация Apple** > **Apple Configurator** > **Профили** > выберите профиль для экспорта > **Экспорт профиля**.
2. В разделе **Прямая регистрация** выберите **Скачать профиль** и сохраните файл.
3. Переместите файл на компьютер Mac с запущенным средством [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12), чтобы отправить его напрямую на устройства iOS как профиль управления.
4. Подготовьте устройство с помощью Apple Configurator, сделав следующее:
    1. На компьютере Mac откройте Apple Configurator 2.0.
    2. Подключите устройство iOS к компьютеру Mac с помощью кабеля USB. При обнаружении устройства закройте средство просмотра фотографий, iTunes и другие приложения, открытые на устройстве.
    3. В Apple Configurator выберите подключенное устройство с iOS и нажмите кнопку **Добавить**. В раскрывающемся списке отображаются параметры, которые могут быть добавлены к устройству. Выберите **Профили**.

        ![Снимок экрана: экспорт профиля для регистрации с использованием помощника по настройке с выделенным URL-адресом профиля](./media/ios-apple-configurator-add-profile.png)

    4. Используйте средство выбора файлов, чтобы выбрать MOBILECONFIG-файл, экспортированный из Intune, и нажмите кнопку **Добавить**. Профиль будет добавлен в устройство. Если устройство настроено как незащищенное, для установки нужно принять условия на устройстве.
5. Следуйте инструкциям ниже, чтобы установить профиль на устройстве iOS. Помощник по настройке уже должен завершить свою работу, и устройство должно быть готово к использованию. Если регистрация влечет за собой развертывания приложений, то у устройства должен быть задан Apple ID, так как для развертывания приложений необходимо выполнить вход в магазин приложений с Apple ID.
    1. Разблокируйте устройство iOS.
    2. В диалоговом окне **Install profile** (Установка профиля) для параметра **Management profile** (Профиль управления) выберите **Install** (Установить).
    3. Укажите секретный код устройства или Apple ID, если это необходимо.
    4. Примите **Предупреждение** и нажмите кнопку **Установить**.
    5. Примите **Удаленное предупреждение** и нажмите кнопку **Доверяю**.
    6. Когда состояние профиля в окне **Profile Installed** (Профиль установлен) изменится на установленный, нажмите кнопку **Done** (Готово).

6. На устройстве iOS откройте экран **Settings** (Параметры) и выберите **General** > **Device Management** > **Management Profile** (Общие > Управление устройством > Профиль управления). Убедитесь в том, что профиль установлен, проверьте ограничения политики iOS и установленные приложения. Для появления на устройстве ограничений политик и приложений может потребоваться до 10 минут.

7. Распределите устройства. Теперь устройство iOS зарегистрировано в Intune и является управляемым.




