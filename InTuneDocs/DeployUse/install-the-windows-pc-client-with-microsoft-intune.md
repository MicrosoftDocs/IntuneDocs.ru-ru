---
# required metadata

title: Установка клиента на компьютере Windows с помощью Microsoft Intune | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 64c11e53-8d64-41b9-9550-4b4e395e8c52

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Установка клиента на компьютере Windows с помощью Microsoft Intune
В этом руководстве содержатся сведения об управлении ПК Windows с помощью клиентского программного обеспечения Microsoft Intune.

## Перед началом работы
Прежде чем начать установку клиентского программного обеспечения Intune, ознакомьтесь с информацией в разделе [Разрешение конфликтов GPO и политик Microsoft Intune](resolve-gpo-and-microsoft-intune-policy-conflicts.md), которая поможет понять, какие компоненты требуются для правильной установки клиента, а затем вернитесь к этим инструкциям.

## Установка клиента
Выполните следующие действия по установке клиента.

-   [Загрузка клиентского программного обеспечения](#to-download-the-client-software)

Затем установите клиент с помощью одного или нескольких указанных далее методов.

-   [Развертывание клиентского программного обеспечения вручную](#to-manually-deploy-the-client-software)

-   [Автоматическое развертывание клиентского программного обеспечения с помощью групповой политики](#to-automatically-deploy-the-client-software-by-using-group-policy)

-   [Самостоятельная регистрация компьютеров пользователями](#how-users-can-self-enroll-their-computers)

-   [Установка клиентского программного обеспечения Microsoft Intune как части образа](#install-the-microsoft-intune-client-software-as-part-of-an-image)

Если управлять компьютером с помощью Intune больше не требуется, компьютер можно снять с учета, в результате чего с него будет удалено клиентское программное обеспечение. Дополнительные сведения см. в разделе [Общие задачи управления ПК Windows с клиентом Microsoft Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).

### Загрузка клиентского программного обеспечения

1.  В [консоли администрирования Microsoft Intune](https://manage.microsoft.com/) щелкните **Администрирование** &gt; **Загрузка клиентского программного обеспечения**.

  ![Загрузка клиентского ПО Intune](./media/pc-SA-client-download.png)

2.  На странице **Загрузка клиентского программного обеспечения** нажмите кнопку **Загрузить клиентское программное обеспечение** и сохраните пакет **Microsoft_Intune_Setup.zip** с ПО в надежной сетевой папке.

    > [!NOTE]
    > Пакет установки клиентского программного обеспечения Intune содержит данные о вашей учетной записи. Если доступ к установочному пакету получат неавторизованные пользователи, они смогут зарегистрировать компьютеры в учетной записи, указанной во внедренном сертификате.

3.  Извлеките содержимое пакета установки и сохраните его в надежной сетевой папке.

    > Не переименовывайте и не перемещайте извлеченный файл **ACCOUNTCERT**, так как в противном случае установка клиентского программного обеспечения будет невозможна.

### Развертывание клиентского программного обеспечения вручную

1.  На компьютере перейдите к папке с файлами установки клиентского программного обеспечения, а затем запустите файл **Microsoft_Intune_Setup.exe**, чтобы установить клиентское программное обеспечение.

    > Состояние установки отображается при наведении указателя мыши на значок на панели задач клиентского компьютера.

### Автоматическое развертывание клиентского программного обеспечения с помощью групповой политики

1.  В папке с файлами **Microsoft_Intune_Setup.exe** и **MicrosoftIntune.accountcert** выполните следующую команду для извлечения программ установки установщика Windows для 32- и 64-разрядных компьютеров.

    ```
    Microsoft_Intune_Setup.exe/Extract <destination folder>
    ```

2.  Скопируйте файлы **Microsoft_Intune_x86.msi**, **Microsoft_Intune_x64.msi** и **MicrosoftIntune.accountcert** в сетевую папку, доступную всем компьютерам, на которых будет установлено клиентское программное обеспечение.

    > Не переименовывайте и не разделяйте файлы, так как в этом случае установка клиентского программного обеспечения не будет выполнена.

3.  С помощью групповой политики разверните программное обеспечение на компьютерах в сети.

    Дополнительные сведения об использовании групповой политики для автоматического развертывания программного обеспечения см. в документации к Windows Server.

### Самостоятельная регистрация компьютеров пользователями
Пользователи могут самостоятельно зарегистрировать свои компьютеры на корпоративном портале Intune. Каждый зарегистрированный компьютер связывается с учетной записью пользователя, которая использовалась для запуска клиентского программного обеспечения.

> [!NOTE]
> -   Пользователь, устанавливающий клиентское программное обеспечение, должен иметь права администратора
> -   Для самостоятельной регистрации на клиентском компьютере должен быть установлен браузер Windows Internet Explorer.
> -   При каждой самостоятельной регистрации компьютера используется лицензия Intune.
> -   Для самостоятельной регистрации компьютера необходимо использовать рабочую учетную запись. Самостоятельную регистрацию компьютера невозможно выполнить с помощью учетной записи Майкрософт.
> -   Если клиентское программное обеспечение уже установлено на компьютере, конечный пользователь получит сообщение об ошибке.

### Самостоятельная регистрация компьютера (сведения для конечных пользователей)

1.  Войдите на корпоративный портал с компьютера, который нужно зарегистрировать.

2.  Нажмите кнопку **Добавить устройство**.

3.  Нажмите кнопку **Загрузить ПО**, а затем нажмите кнопку **Выполнить**.

4.  Для запуска мастера установки нажмите кнопку **Далее**.

5.  После завершения работы мастера установки нажмите кнопку **Готово**.

### Установка клиентского программного обеспечения Microsoft Intune как части образа
Клиентское программное обеспечение Intune можно развернуть в составе образа операционной системы, выполнив следующую приведенную в качестве примера процедуру.

1.  Скопируйте файлы установки клиента, **Microsoft_Intune_Setup.exe** и **MicrosoftIntune.accountcert**, в папку **%Systemdrive%\Temp\Microsoft_Intune_Setup** на эталонном компьютере.

2.  Создайте запись реестра **WindowsIntuneEnrollPending** , добавив в сценарий **SetupComplete.cmd** следующую команду:

    ```
    %windir%\system32\reg.exe add HKEY_LOCAL_MACHINE\Software\Microsoft\Onlinemanagement\Deployment /v
    WindowsIntuneEnrollPending /t REG_DWORD /d 1
    ```

3.  Добавьте следующую команду в сценарий **setupcomplete.cmd**, чтобы запустить пакет регистрации с аргументом /PrepareEnroll:

    ```
    %systemdrive%\temp\Microsoft_Intune_Setup\Microsoft_Intune_Setup.exe /PrepareEnroll
    ```
    > [!TIP]
    > Сценарий **SetupComplete.cmd** позволяет программе установки Windows вносить изменения в систему до того, как пользователь выполнит вход. Аргумент командной строки **/PrepareEnroll** подготавливает целевой компьютер к автоматической регистрации в Intune после того, как программа установки Windows завершит работу.

4.  Поместите **SetupComplete.cmd** в папку **%Windir%\Setup\Scripts** на эталонном компьютере.

5.  Запишите образ эталонного компьютера, а затем разверните его на целевых компьютерах.

После перезагрузки целевого компьютера по завершении выполнения программы установки Windows будет создан раздел реестра **WindowsIntuneEnrollPending** . Пакет регистрации проверяет, зарегистрирован ли компьютер. Если компьютер зарегистрирован, дальнейшие действия не предпринимаются. Если компьютер не зарегистрирован, пакет регистрации создает задачу автоматической регистрации в Microsoft Intune.

При следующем запланированном запуске задачи автоматической регистрации выполняется проверка на наличие параметра реестра **WindowsIntuneEnrollPending** и предпринимается попытка регистрации целевого компьютера в Intune. Если по какой-либо причине выполнить регистрацию не удается, при следующем запуске задачи будет предпринята повторная попытка. Попытки продолжаются в течение одного месяца.

После успешной регистрации или через один месяц задача автоматической регистрации Intune, значение реестра **WindowsIntuneEnrollPending** и сертификат учетной записи удаляются с целевого компьютера.

## Отслеживание и проверка успешного развертывания клиента
Для отслеживания и проверки успешного развертывания клиента можно использовать любую из следующих процедур.

### Проверка установки клиентского программного обеспечения с консоли администрирования Microsoft Intune

1.  На [консоли администрирования Microsoft Intune](https://manage.microsoft.com/) щелкните **Группы** &gt; **Все устройства** &gt; **Все компьютеры**.

2.  В списке компьютеров найдите управляемые компьютеры, взаимодействующие с Intune. Кроме того, можно найти конкретный управляемый компьютер, указав его имя целиком (или любую часть имени) в поле **Поиск устройств**.

3.  Проверьте состояние компьютера в нижней части консоли и устраните возможные ошибки.

### Создание отчета об инвентаризации компьютеров для отображения всех зарегистрированных компьютеров

1.  На [консоли администрирования Microsoft Intune](https://manage.microsoft.com/) щелкните **Отчеты** &gt; **Отчеты об инвентаризации компьютеров**.

2.  На странице **Создание отчета** оставьте все значения по умолчанию (если не требуется применять фильтры) и нажмите кнопку **Просмотреть отчет**.

3.  В новом окне откроется страница **Отчет об инвентаризации компьютеров** со списком всех компьютеров, успешно зарегистрированных в Intune.

    > Чтобы отсортировать список по содержимому столбца, щелкните заголовок столбца.


### См. также
[Управление ПК под управлением Windows с помощью Microsoft Intune](manage-windows-pcs-with-microsoft-intune.md)


<!--HONumber=May16_HO2-->

