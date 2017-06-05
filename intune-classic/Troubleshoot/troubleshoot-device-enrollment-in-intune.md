---
title: "Устранение проблем при регистрации устройств | Документы Майкрософт"
description: "Рекомендации по устранению неполадок с регистрацией устройств."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 05/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6982ba0e-90ff-4fc4-9594-55797e504b62
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: e72051f9318d24ed36fc39ea6645041f0a150a40
ms.contentlocale: ru-ru
ms.lasthandoff: 05/23/2017


---

# <a name="troubleshoot-device-enrollment-in-intune"></a>Устранение проблем при регистрации устройств в Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

В этом разделе приводятся рекомендации по устранению неполадок с регистрацией устройств. Если эти сведения не позволяют решить проблему, см. дополнительные справочные материалы в статье [Получение поддержки для Microsoft Intune](how-to-get-support-for-microsoft-intune.md).


## <a name="initial-troubleshooting-steps"></a>Первые действия по устранению неполадок

Прежде чем приступать к устранению неполадок, убедитесь, что в Intune должным образом настроена регистрация. О требованиях к настройке можно прочитать в следующих разделах.

-    [Подготовка к регистрации устройств в Microsoft Intune](/intune-classic/deploy-use/prerequisites-for-enrollment)
-    [Настройка управления устройствами в iOS на Mac](/intune-classic/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)
-    [Настройка управления устройствами в Windows](/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune)
-    [Настройка управления устройствами с Android](/intune-classic/deploy-use/set-up-android-management-with-microsoft-intune) —дополнительные действия не требуются
-    [Настройка управления устройствами с Android for Work](/intune-classic/deploy-use/set-up-android-for-work)

Пользователи управляемых вами устройств могут собирать данные из журналов регистрации и диагностики для дальнейшей проверки. Инструкции по сбору данных журналов для пользователей приведены в следующих статьях:

- [Отправка ошибок регистрации устройств с ОС Android ИТ-администратору](https://docs.microsoft.com/intune-user-help/send-enrollment-errors-to-your-it-admin-android)
- [Отправка ошибок на устройствах с ОС iOS ИТ-администратору](https://docs.microsoft.com/intune-user-help/send-errors-to-your-it-admin-ios)


## <a name="general-enrollment-issues"></a>Распространенные проблемы с регистрацией
Эти проблемы могут возникать на всех платформах устройств.

### <a name="device-cap-reached"></a>Достигнут предел для устройств
**Проблема:** во время регистрации на устройстве произошла ошибка, например ошибка **Корпоративный портал временно недоступен** на устройстве iOS, а файл DMPdownloader.log в Configuration Manager содержит ошибку **DeviceCapReached**.

**Решение:**

#### <a name="check-number-of-devices-enrolled-and-allowed"></a>Проверка количества зарегистрированных и разрешенных устройств.

1.  На портале администрирования Intune убедитесь, что пользователь имеет не более 15 (допустимое количество) назначенных устройств.

2.  В консоли администрирования Intune в разделе **Администрирование** > **Управление мобильными устройствами** > **Правила регистрации** убедитесь, что для параметра "Предел для регистрации устройств" задано значение 15.

<!--- Mobile device users can delete devices at the following URL: [https://byodtestservice.azurewebsites.net/](https://byodtestservice.azurewebsites.net/). --->

Администраторы могут удалять устройства на портале Azure Active Directory.

#### <a name="to-delete-devices-in-the-azure-active-directory-portal"></a>Порядок удаления устройств на портале Azure Active Directory

1.  Перейдите по адресу [http://aka.ms/accessaad](http://aka.ms/accessaad) или выберите **Администрирование** &gt; **Azure AD** на странице [https://portal.office.com](https://portal.office.com).

2.  Выполните вход с помощью кода организации, используя ссылку в левой части страницы.

3.  Создайте подписку Azure (если у вас ее еще нет), щелкнув ссылку **Register your free Azure Active Directory** (Зарегистрировать бесплатную версию Azure Active Directory). Если у вас платная учетная запись, то платить кредитной картой или иным способом не потребуется.

4.  Выберите **Active Directory**, а затем выберите вашу организацию.

5.  Откройте вкладку **Пользователи**.

6.  Выберите пользователя, устройства которого требуется удалить.

7.  Выберите **Устройства**.

8.  Удалите соответствующие устройства, например неиспользуемые или имеющие неверные определения.

> [!NOTE]

> Можно избежать достижения предельного значения регистрации устройств с помощью учетной записи диспетчера регистрации устройств, как описано в статье [Регистрация корпоративных устройств с помощью диспетчера регистрации устройств в Microsoft Intune](/intune-classic/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).
>
> Учетная запись, добавленная в учетную запись диспетчера регистрации устройств, не сможет завершить регистрацию при применении политики условного доступа для этого конкретного имени для входа.

### <a name="company-portal-temporarily-unavailable"></a>Корпоративный портал временно недоступен
**Проблема:** на устройстве появляется ошибка **Корпоративный портал временно недоступен**.

**Решение:**

1.  Удалите приложение корпоративного портала с устройства.

2.  Откройте на устройстве браузер, перейдите по адресу [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com)и повторите попытку входа пользователя.

3.  Если пользователю не удается войти, попросите его попробовать другую сеть.

4.  В случае неудачи убедитесь, что учетные данные пользователя правильно синхронизированы с Azure Active Directory.

5.  Если пользователь успешно входит в систему, устройство iOS предлагает установить приложение корпоративного портала и выполнить регистрацию. На устройстве с Android необходимо вручную установить приложение корпоративного портала Intune, после чего можно повторить попытку регистрации.

### <a name="mdm-authority-not-defined"></a>Центр управления мобильными устройствами не определен
**Проблема:** появляется ошибка **MDM authority not defined** (Центр MDM не определен).

**Решение:**

1.  Убедитесь, что Центр MDM должным образом настроен в той версии службы Intune, которую вы используете (то есть для Intune, Office 365 или System Center Configuration Manager с Intune). Для Intune Центр MDM задается в разделе **Администрирование** &gt; **Управление мобильными устройствами**. Для Configuration Manager с Intune он задается при настройке соединителя с Intune, а в Office 365 — при помощи параметра **Мобильные устройства**.

    > [!NOTE]
    > После задания Центра MDM его можно изменить, только обратившись в службу поддержки, как описано в статье [Получение поддержки для Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

2.  Убедитесь, что учетные данные пользователя правильно синхронизированы с Azure Active Directory. Для этого имя субъекта-пользователя конкретного пользователя должно совпадать с данными Active Directory на портале Office 365.
    Если имя участника-пользователя не соответствует сведениям Active Directory:

    1.  Отключите DirSync на локальном сервере.

    2.  Удалите несоответствующего пользователя из списка пользователей на **портале учетных записей Intune** .

    3.  Подождите около одного часа, чтобы дать службе Azure возможность удалить неправильные данные.

    4.  Снова включите DirSync и проверьте правильность синхронизации пользователя.

3.  В сценарии, где вы используете System Center Configuration Manager с Intune, убедитесь, что пользователь имеет допустимый облачный идентификатор пользователя:

    1.  Откройте SQL Management Studio.

    2.  Подключитесь к соответствующей базе данных.

    3.  Откройте папку баз данных, а затем найдите и откройте папку **CM_DBName**, где DBName — это имя базы данных клиента.

    4.  В верхней части окна выберите **Создать запрос** и выполните следующие запросы:

        -   Для просмотра всех пользователей: `select * from [CM_ DBName].[dbo].[User_DISC]`

        -   Для просмотра отдельных пользователей используйте следующий запрос, где %testuser1% представляет username@domain.com для пользователя, которого вы хотите найти: `select * from [CM_ DBName].[dbo].[User_DISC] where User_Principal_Name0 like '%testuser1%'`

        Написав запрос, нажмите кнопку **!Выполнить**.
        После возвращения результатов найдите идентификатор clouduser.  Если этот идентификатор не найден, пользователь не имеет лицензии на использование Intune.

### <a name="unable-to-create-policy-or-enroll-devices-if-the-company-name-contains-special-characters"></a>Не удается создать политику или зарегистрировать устройство, если название организации содержит специальные символы
**Проблема:** не удается создать политику или зарегистрировать устройства.

**Решение:** в [Центре администрирования Office 365](https://portal.office.com/) удалите специальные символы из имени организации и сохраните сведения об организации.

### <a name="unable-to-log-in-or-enroll-devices-when-you-have-multiple-verified-domains"></a>Не удается выполнить вход или регистрацию устройств при наличии нескольких проверенных доменов
**Проблема:** при добавлении второго проверенного домена в AD FS пользователи с суффиксом имени субъекта-пользователя (UPN) этого второго домена могут не иметь возможности входить на порталы или регистрировать устройства.


**Решение**. Клиентам Microsoft Office 365, использующим единый вход (SSO) через AD FS 2.0 и имеющим несколько доменов верхнего уровня для UPN-суффиксов пользователей в организации (например, @contoso.com или @fabrikam.com), следует развернуть отдельный экземпляр службы федерации AD FS 2.0 для каждого суффикса. Сейчас существует [свертка для AD FS 2.0](http://support.microsoft.com/kb/2607496), работающая совместно с параметром **SupportMultipleDomain**, чтобы сервер AD FS поддерживал этот сценарий без дополнительных серверов AD FS 2.0. Дополнительные сведения см. в [этом блоге](https://blogs.technet.microsoft.com/abizerh/2013/02/05/supportmultipledomain-switch-when-managing-sso-to-office-365/).


## <a name="android-issues"></a>Проблемы в Android
### <a name="devices-fail-to-check-in-with-the-intune-service-and-display-as-unhealthy-in-the-intune-admin-console"></a>Устройствам не удается обратиться к службе Intune. В консоли администрирования Intune для них отображается состояние "Неработоспособное"
**Проблема:** некоторые устройства Samsung под управлением Android 4.4.x и 5.x могут прекратить обращаться к службе Intune. Устройства не обращаются в следующих случаях:

- Они не могут принимать политику, приложения и удаленные команды из службы Intune.
- В консоли администрирования для них отображается состояние управления **Неработоспособное**.
- Пользователи, защищенные с помощью политик условного доступа, могут потерять доступ к корпоративным ресурсам.

Компания Samsung подтвердила, что программа Samsung Smart Manager, поставляемая на некоторых устройствах Samsung, может привести к отключению корпоративного портала Intune и его компонентов. Когда корпоративный портал отключен, он не может выполняться в фоновом режиме и не может подключиться к службе Intune.

**Решение №1**

Попросите пользователей вручную запустить приложение корпоративного портала. При перезапуске приложения устройство обращается к службе Intune.

> [!IMPORTANT]
> Открывание приложения корпоративного портала вручную — это временное решение, так как Samsung Smart Manager может снова отключить его.

**Решение №2**

Попросите пользователей обновить операционную систему устройства до версии Android 6.0. Указанная проблема не возникает на устройствах с Android 6.0. Чтобы проверить, доступно ли обновление, пользователи могут выбрать **Параметры** > **About device**(Об устройстве) > **Download updates manually** (Скачивание обновлений вручную) и следовать указаниям в устройстве.

**Решение №3**

Если решение №2 не сработает, попросите пользователей исключить приложение корпоративного портала из Smart Manager, сделав следующее:

1. Запустите приложение Smart Manager на устройстве.

  ![Выберите значок Smart Manager](./media/smart-manager-app-icon.png)

2. Выберите плитку **Батарея**.

  ![Выберите плитку "Батарея"](./media/smart-manager-battery-tile.png)

3. В разделе **App power saving** (Энергосбережение приложения) или **App optimization** (Оптимизация приложения) выберите **Сведения**.

  ![В разделе App power saving (Энергосбережение приложения) или App optimization (Оптимизация приложения) выберите "Сведения"](./media/smart-manager-app-power-saving-detail.png)

4. В списке приложений выберите **Корпоративный портал**.

  ![В списке приложений выберите "Корпоративный портал"](./media/smart-manager-company-portal.png)

5. Установите переключатель **Отключен**.

  ![Установите переключатель "Отключен" в диалоговом окне App optimization (Оптимизация приложения)](./media/smart-manager-app-optimization-turned-off.png)

6. В разделе **App power saving** (Энергосбережение приложения) или **App optimization** (Оптимизация приложения) убедитесь, что корпоративный портал отключен.

  ![Убедитесь, что корпоративный портал отключен](./media/smart-manager-verify-comp-portal-turned-off.png)


### <a name="profile-installation-failed"></a>Сбой установки профиля
**Проблема:** на устройстве с Android появляется ошибка **Сбой установки профиля**.

**Решение:**

1.  Убедитесь, что пользователю назначена соответствующая лицензия для той версии службы Intune, которую вы используете.

2.  Убедитесь, что устройство не зарегистрировано у другого поставщика MDM и не имеет установленного профиля управления.

3.  Убедитесь, что в качестве браузера по умолчанию выбран Chrome для Android и включены файлы cookie.

### <a name="android-certificate-issues"></a>Проблемы с сертификатом Android

**Проблема**. На устройстве пользователя отобразилось следующее сообщение: *Вход невозможен, так как у вашего устройства нет необходимого сертификата*.

**Решение 1**.

Попросите пользователя выполнить инструкции из раздела [Устройство не имеет необходимого сертификата](/intune-user-help/your-device-is-missing-a-required-certificate-android#your-device-is-missing-a-certificate-required-by-your-it-administrator). Если ошибка появляется после выполнения пользователем указанных инструкций, попробуйте воспользоваться решением 2.

**Решение 2**.

Если пользователи по-прежнему видят сообщение об отсутствующем сертификате после ввода своих корпоративных учетных данных и перехода к процедуре федеративного входа, возможно, на сервере служб федерации Active Directory (AD FS) отсутствует промежуточный сертификат.

Ошибка сертификата вызвана тем, что устройства Android требуют включения промежуточных сертификатов в [приветствие сервера SSL](https://technet.microsoft.com/library/cc783349.aspx), однако сейчас сервер по умолчанию AD FS или прокси-сервер AD FS отправляет в ответе на приветствие клиента SSL только SSL-сертификат службы AD FS.

Чтобы устранить эту проблему, импортируйте сертификаты в хранилище личных сертификатов компьютеров на сервере AD FS или прокси-серверах следующим образом:

1.    На серверах ADFS и прокси-серверах запустите консоль управления сертификатами для локального компьютера, щелкнув правой кнопкой мыши кнопку **Пуск**, выбрав элемент **Выполнить** и введя **certlm.msc**.
2.    Разверните узел **Личный** и щелкните **Сертификаты**.
3.    Найдите сертификат для связи со службой AD FS (сертификат с открытой подписью) и дважды щелкните для просмотра его свойств.
4.    Выберите **Путь сертификации**, чтобы просмотреть родительские сертификаты данного сертификата.
5.    Для каждого родительского сертификата выберите **Просмотр сертификата**.
6.    Перейдите на вкладку **Сведения** и выберите **Копировать в файл…**
7.    Следуйте указаниям мастера для экспорта или сохранения открытого ключа сертификата в требуемое расположение.
8.    Импортируйте родительские сертификаты, которые были экспортированы на шаге 3, в папку Local Computer\Personal\Certificates, щелкнув правой кнопкой мыши элемент **Сертификаты**, выбрав **Все задачи** > **Импорт**, а затем выполнив указания мастера по импорту сертификатов.
9.    Перезапустите серверы AD FS.
10.    Повторите описанные выше действия на всех серверах AD FS и прокси-серверах.
Теперь пользователь сможет войти на корпоративный портал с устройства Android.

**Проверка правильности установки сертификата**:

Ниже описан лишь один из многих методов, которые можно использовать для проверки правильной установки сертификата.

1. Перейдите в [бесплатное средство Digicert](ttps://www.digicert.com/help/).
2. Введите полное доменное имя сервера AD FS (например, sts.contoso.com) и выберите **CHECK SERVER** (Проверить сервер).

Если сертификат сервера установлен правильно, в списке результатов отображаются только галочки. При наличии проблем в разделах отчета "Certificate Name Matches" (Совпадение имени сертификата) и "SSL Certificate is correctly Installed" (Правильная установка SSL-сертификата) отображается красный значок X.


## <a name="ios-issues"></a>Проблемы в iOS

### <a name="ios-enrollment-errors"></a>Ошибки регистрации iOS
В следующей таблице приведены ошибки, с которыми конечные пользователи могут столкнуться при регистрации устройств iOS в Intune.

|Сообщение об ошибке|Проблема|Разрешение|
|-----------------|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
|NoEnrollmentPolicy|Политика регистрации не найдена|Убедитесь в том, что все предварительные условия для регистрации выполнены, в частности, имеется сертификат APNs и включен параметр "iOS как платформа". Инструкции см. в статье [Настройка управления устройствами в iOS и Mac](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune).|
|DeviceCapReached|Вы уже зарегистрировали слишком много мобильных устройств.|Пользователь должен удалить одно из уже зарегистрированных мобильных устройств с корпоративного портала перед регистрацией следующего. См. инструкции по типу используемого устройства: [Android](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-android), [iOS](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-ios), [Windows](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-windows).|
|APNSCertificateNotValid|Возникла проблема с сертификатом, который позволяет мобильному устройству взаимодействовать с корпоративной сетью.<br /><br />|Служба Apple Push Notification Service (APNs) предоставляет возможность доступа к зарегистрированным устройствам iOS. Если действия по получению сертификата APNs выполнены не были или истек срок его действия, попытки регистрации завершатся выводом этого сообщения об ошибке.<br /><br />Просмотрите сведения о настройке пользователей в статьях [Синхронизация Active Directory и добавление пользователей в Intune](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-3) и [Организация пользователей и устройств](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-5).|
|AccountNotOnboarded|Возникла проблема с сертификатом, который позволяет мобильному устройству взаимодействовать с корпоративной сетью.<br /><br />|Служба Apple Push Notification Service (APNs) предоставляет возможность доступа к зарегистрированным устройствам iOS. Если действия по получению сертификата APNs выполнены не были или истек срок его действия, попытки регистрации завершатся выводом этого сообщения об ошибке.<br /><br />Дополнительные сведения см. в статье [Настройка управления устройствами iOS и Mac с помощью Microsoft Intune](/Intune/Deploy-use/set-up-ios-and-mac-management-with-microsoft-intune).|
|DeviceTypeNotSupported|Возможно, пользователь попытался зарегистрировать устройство без iOS. Тип регистрируемого мобильного устройства не поддерживается.<br /><br />Убедитесь, что устройство работает под управлением iOS версии 8.0 или более поздней.<br /><br />|Убедитесь, что устройство пользователя работает под управлением iOS версии 8.0 или более поздней.|
|UserLicenseTypeInvalid|Нельзя зарегистрировать устройство, так как ваша учетная запись еще не входит в нужную группу пользователей.<br /><br />|Чтобы пользователь мог зарегистрировать свое устройство, он должен быть участником соответствующей группы пользователей. Это сообщение означает, что пользователь располагает неправильным типом лицензии для назначенного центра управления мобильными устройствами. Например, если в качестве центра управления мобильными устройствами назначен Intune, а пользователь использует System Center 2012 R2 Configuration Manager, появится указанное сообщение об ошибке.<br /><br />Дополнительные сведения см. в следующих источниках:<br /><br />Изучите статью, посвященную [настройке управления устройствами c iOS и Mac OS с помощью Microsoft Intune](/Intune/Deploy-use/set-up-ios-and-mac-management-with-microsoft-intune), а также сведения о настройке пользователей в статьях [Синхронизация Active Directory и добавление пользователей в Intune](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-3) и [Организация пользователей и устройств](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-5).|
|MdmAuthorityNotDefined|Центр управления мобильными устройствами не определен.<br /><br />|В Intune не был назначен центр управления мобильными устройствами.<br /><br />См. пункт 1 в разделе "Шаг 6: регистрация мобильных устройств и установка приложения" статьи [Начало работы с 30-дневной пробной версии Microsoft Intune](/Intune/Understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune).|

### <a name="devices-are-inactive-or-the-admin-console-cannot-communicate-with-them"></a>Устройства неактивны, или консоль администрирования не может связаться с ними
**Проблема:** устройства с ОС iOS не отмечаются в службе Intune. Устройства должны периодически отмечаться в службе для сохранения доступа к защищенным ресурсам компании. Если устройства не отмечаются в службе:

- Они не могут принимать политику, приложения и удаленные команды из службы Intune.
- В консоли администрирования для них отображается состояние управления **Неработоспособное**.
- Пользователи, защищенные с помощью политик условного доступа, могут потерять доступ к корпоративным ресурсам.

**Решение:** предоставьте следующие решения конечным пользователям, чтобы они могли вернуть доступ к ресурсам организации.

При запуске приложения "Корпоративный портал" в iOS пользователи могут получить сообщение, что устройство потеряло связь с Intune. В этом случае оно автоматически попытается синхронизироватся с Intune для восстановления подключения, и появится встроенное уведомление **Выполняется попытка синхронизации…** .

  ![Уведомление "Выполняется попытка синхронизации"](./media/ios_cp_app_trying_to_sync_notification.png)

При успешной синхронизации в приложении "Корпоративный портал" в iOS появится встроенное уведомление **Синхронизация выполнена**. Это значит, что устройство находится в работоспособном состоянии.

  ![Уведомление "Синхронизация выполнена"](./media/ios_cp_app_sync_successful_notification.png)

Если выполнить синхронизацию не удалось, появится встроенное уведомление **Не удалось синхронизировать** в приложении "Корпоративный портал" в iOS.

  ![Уведомление "Не удалось синхронизировать"](./media/ios_cp_app_unable_to_sync_notification.png)

Чтобы устранить эту проблему, пользователям нужно нажать кнопку **Настроить** справа от уведомления **Не удалось синхронизировать**. Нажав ее, пользователи перейдут на экран "Настройка доступа к ресурсам организации" с инструкциями по регистрации устройства.

  ![Экран "Настройка доступа к ресурсам организации"](./media/ios_cp_app_company_access_setup.png)

После регистрации устройства перейдут в работоспособное состояние и снова получат доступ к ресурсам организации.

### <a name="verify-ws-trust-13-is-enabled"></a>Убедитесь, что включен WS-Trust 1.3
**Проблема**. Не удается зарегистрировать устройства с iOS с поддержкой программы регистрации устройств (DEP)

Регистрация устройств DEP с сопоставлением пользователей требует включения конечной точки WS-Trust 1.3 в режиме "Имя пользователя/Смешанный" для запроса токенов пользователя. Active Directory включает эту конечную точку по умолчанию. Получить список задействованных конечных точек можно с помощью командлета PowerShell Get-AdfsEndpoint и поиска конечной точки trust/13/UsernameMixed. Пример.

      Get-AdfsEndpoint -AddressPath “/adfs/services/trust/13/UsernameMixed”

Дополнительные сведения см. в [документации Get-AdfsEndpoint](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

Дополнительные сведения см. в статье [Рекомендации по защите служб федерации Active Directory](https://technet.microsoft.com/windows-server-docs/identity/ad-fs/operations/best-practices-securing-ad-fs). Если требуется дополнительная помощь для определения, включена ли у вашего поставщика удостоверений федерации конечная точка WS-Trust 1.3 в режиме "Имя пользователя/Смешанный", обратитесь в службу технической поддержки Майкрософт при использовании служб ADFS или к стороннему поставщику удостоверений.


### <a name="profile-installation-failed"></a>Сбой установки профиля
**Проблема:** на устройстве с iOS появляется ошибка **Сбой установки профиля**.

### <a name="troubleshooting-steps-for-failed-profile-installation"></a>Действия по устранению неполадок в случае сбоя установки профиля

1.  Убедитесь, что пользователю назначена соответствующая лицензия для той версии службы Intune, которую вы используете.

2.  Убедитесь, что устройство не зарегистрировано у другого поставщика MDM и не имеет установленного профиля управления.

3.  Перейдите по адресу [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com) и попробуйте установить профиль при появлении запроса.

4.  Убедитесь, что в качестве браузера по умолчанию выбран Safari для iOS и включены файлы cookie.

### <a name="enrolled-ios-device-doesnt-appear-in-console-when-using-system-center-configuration-manager-with-intune"></a>Зарегистрированное устройство iOS не отображается в консоли при использовании System Center Configuration Manager с Intune
**Проблема:** пользователь регистрирует устройство iOS, но оно не отображается в консоли администрирования Configuration Manager. Устройство не сообщает о регистрации. Возможные причины.

- Соединитель Microsoft Intune на сайте Configuration Manager не обменивается данными со службой Intune.
- Компонент Data Discovery Manager (ddm) или компонент State Manager (statmgr) не обрабатывают сообщения службы Intune.
- Возможно, вы скачали сертификат MDM из одной учетной записи, а использовали в другой.


**Решение.** Просмотрите следующие файлы журналов на предмет возможных ошибок:

- dmpdownloader.log
- ddm.log
- statmgr.log

Примеры того, что искать в этих файлах журнала, будут добавлены в ближайшее время.


## <a name="issues-when-using-system-center-configuration-manager-with-intune"></a>Проблемы при использовании System Center Configuration Manager с Intune
### <a name="mobile-devices-disappear"></a>Мобильные устройства исчезают
**Проблема:** после успешной регистрации мобильного устройства в Configuration Manager оно пропадает из коллекции мобильных устройств, однако по-прежнему имеет профиль управления и отображается на шлюзе CSS.

**Решение:** это может произойти из-за того, что у вас есть пользовательский процесс, удаляющий не присоединенные к домену устройства, либо пользователь прекратил использование устройства в рамках подписки. Чтобы узнать, какой процесс или какая учетная запись пользователя удалили устройство из консоли Configuration Manager, выполните следующие действия:

#### <a name="check-how-device-was-removed"></a>Определение способа удаления устройства

1.  В консоли администрирования Configuration Manager выберите **Мониторинг** &gt; **Состояние системы** &gt; **Запросы сообщения о состоянии**.

2.  Щелкните элемент **Вручную удаленные ресурсы членов коллекций** правой кнопкой мыши и выберите пункт **Показать сообщения**.

3.  Выберите соответствующую дату и время или период за последние 12 часов.

4.  Найдите требуемое устройство и определите, как оно было удалено. В приведенном ниже примере показано, что устройство удалила учетная запись SCCMInstall с помощью неизвестного приложения.

    ![Снимок экрана для диагностики удаления устройства](./media/CM_With_Intune_Unknown_App_Deleted_Device.jpg)

5.  Убедитесь, что в Configuration Manager отсутствует запланированная задача, скрипт или другой процесс, которые могут выполнять автоматическую очистку недоменных, мобильных или связанных устройств.




### <a name="other-ios-enrollment-errors"></a>Другие ошибки регистрации в iOS
Список ошибок регистрации в iOS приведен в документации по устройствам для пользователей в статье [You see errors while trying to enroll your device in Intune](/intune-user-help/using-your-iOS-or-macOS-device-with-intune) (Ошибки при попытке регистрации устройства в Intune).

## <a name="pc--issues"></a>Проблемы с компьютером

### <a name="the-machine-is-already-enrolled---error-hr-0x8007064c"></a>Компьютер уже зарегистрирован — ошибка hr 0x8007064c
**Проблема:** регистрация завершается с ошибкой **компьютер уже зарегистрирован**. В журнале регистрации присутствует ошибка **hr 0x8007064c**.

Возможно, компьютер уже был зарегистрирован ранее, или существует клонированный образ компьютера, который и был зарегистрирован. На компьютере все еще находится сертификат предыдущей учетной записи.



**Решение:**

1. В меню **Пуск** щелкните **Выполнить** ->  и введите **MMC**.
1. Выберите **Файл** > **Добавление и удаление оснасток**.
1. Дважды щелкните **Сертификаты**, выберите **Учетная запись компьютера** > **Далее** и выберите **Локальный компьютер**.
1. Дважды щелкните **Сертификаты (локальный компьютер)** и выберите **Личные/Сертификаты**.
1. Выполните поиск сертификата Intune, выданного Sc_Online_Issuing, и удалите его, если он существует.
1. Удалите этот раздел реестра, если он существует, а также все его подразделы: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\OnlineManagement regkey**.
1. Попробуйте зарегистрироваться еще раз.
1. Если компьютер по-прежнему невозможно зарегистрировать, найдите и удалите этот раздел, если он существует: **KEY_CLASSES_ROOT\Installer\Products\6985F0077D3EEB44AB6849B5D7913E95**.
1. Попробуйте зарегистрироваться еще раз.

    > [!IMPORTANT]
    > В этом разделе, методе или задаче описывается внесение изменений в реестр. При неправильном изменении реестра могут возникнуть серьезные проблемы. Поэтому будьте внимательны и в точности следуйте инструкциям. Для дополнительной защиты заархивируйте реестр перед внесением изменений. Это позволит восстановить реестр, если возникнут проблемы.
    > Дополнительные сведения об архивации и восстановлении реестра см. в статье [How to back up and restore the registry in Windows](https://support.microsoft.com/kb/322756) (Архивация и восстановление реестра в Windows).

## <a name="general-enrollment-error-codes"></a>Коды общих ошибок регистрации

|Код ошибки|Возможная проблема|Предлагаемое решение|
|--------------|--------------------|----------------------------------------|
|0x80CF0437 |На клиентском компьютере установлено неправильное время.|Убедитесь в правильности установки времени и часового пояса на клиентском компьютере.|
|0x80240438, 0x80CF0438, 0x80CF402C|Не удается подключиться к службе Intune. Проверьте параметры прокси-сервера на клиентском компьютере.|Убедитесь, что конфигурация прокси-сервера на клиентском компьютере поддерживается Intune, и проверьте наличие доступа к Интернету с клиентского компьютера.|
|0x80240438, 0x80CF0438|Параметры прокси-сервера в браузере Internet Explorer и в локальной системе не настроены.|Не удается подключиться к службе Intune. Проверьте параметры прокси-сервера для клиента и убедитесь, что конфигурация прокси-сервера на клиентском компьютере поддерживается Intune, а также проверьте наличие доступа к Интернету с клиентского компьютера.|
|0x80043001, 0x80CF3001, 0x80043004, 0x80CF3004|Пакет регистрации устарел.|Скачайте и установите текущую версию клиентского программного обеспечения в рабочей области "Администрирование".|
|0x80043002, 0x80CF3002|Учетная запись находится в режиме обслуживания.|Если учетная запись находится в режиме обслуживания, невозможно зарегистрировать новые клиентские компьютеры. Для просмотра параметров учетной записи выполните вход в нее.|
|0x80043003, 0x80CF3003|Учетная запись удалена.|Убедитесь, что срок действия учетной записи и подписки на Intune не истек. Для просмотра параметров учетной записи выполните вход в нее.|
|0x80043005, 0x80CF3005|Клиентский компьютер был списан.|Подождите несколько часов, удалите все прежние версии клиентского программного обеспечения с компьютера и затем снова попытайтесь установить клиентское программное обеспечение.|
|0x80043006, 0x80CF3006|Превышено максимальное число рабочих мест для учетной записи организации.|Перед регистрацией дополнительных клиентских компьютеров в службе необходимо приобрести дополнительные рабочие места.|
|0x80043007, 0x80CF3007|Не удалось найти файл сертификата в папке программы установщика.|Извлеките все файлы перед началом установки. Не переименовывайте и не перемещайте извлеченные файлы; все файлы должны находиться в одной папке, в противном случае установка будет невозможна.|
|0x8024D015, 0x00240005, 0x80070BC2, 0x80070BC9, 0x80CFD015|Не удается установить клиентское программное обеспечение, поскольку ожидается перезагрузка клиентского компьютера.|Перезагрузите компьютер и затем снова попытайтесь установить клиентское программное обеспечение.|
|0x80070032|Не удалось найти как минимум один обязательный компонент для установки клиентского программного обеспечения на клиентском компьютере.|Убедитесь, что на клиентском компьютере установлены все требуемые обновления и затем снова попытайтесь установить клиентское программное обеспечение.|
|0x80043008, 0x80CF3008|Не удалось запустить службу Microsoft Online Management Updates.|Обратитесь в службу поддержки Майкрософт, как описано в статье [Как получить поддержку для Microsoft Intune](how-to-get-support-for-microsoft-intune.md).|
|0x80043009, 0x80CF3009|Клиентский компьютер уже зарегистрирован в службе.|Перед повторной регистрацией компьютера в службе необходимо снять его с учета.|
|0x8004300B, 0x80CF300B|Невозможно запустить пакет установки клиентского программного обеспечения, так как версия ОС Windows, установленная на клиентском компьютере, не поддерживается.|Intune не поддерживает версию ОС Windows, установленную на клиентском компьютере.|
|0xAB2|Установщику Windows не удалось получить доступ к среде выполнения VBScript для выполнения настраиваемого действия.|Эта ошибка вызвана настраиваемым действием на основе библиотек динамической компоновки (DLL). При устранении неполадок, связанных с библиотекой DLL, могут быть полезны средства, описанные в [статье 198038 базы знаний на сайте поддержки Майкрософт: "Полезные средства для решения вопросов упаковки и развертывания"](https://support.microsoft.com/kb/198038).|
|0x80cf0440|Подключение к конечной точке службы завершено.|Действие пробной или платной учетной записи приостановлено. Создайте новую пробную или платную учетную запись и повторите регистрацию.|




### <a name="next-steps"></a>Дальнейшие действия
Если эта информация не помогла, обратитесь в службу поддержки Майкрософт, как описано в статье [Получение поддержки для Microsoft Intune](how-to-get-support-for-microsoft-intune.md).
