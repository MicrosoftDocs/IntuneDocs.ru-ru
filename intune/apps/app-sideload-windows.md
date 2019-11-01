---
title: Загрузка неопубликованных приложений Windows и Windows Phone
titleSuffix: Microsoft Intune
description: Узнайте, как подписывать бизнес-приложения, чтобы использовать Intune для их развертывания.
keywords: ''
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 09/24/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: e44f1756-52e1-4ed5-bf7d-0e80363a8674
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4a89392dabe695cf49e989351cef822852676916
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72507383"
---
# <a name="sign-line-of-business-apps-so-they-can-be-deployed-to-windows-devices-with-intune"></a>Подписывание бизнес-приложений для развертывания на устройствах Windows с помощью Intune

[!INCLUDE [both-portals](../../intune-classic/includes/note-for-both-portals.md)]

Администратор Intune может развертывать универсальные бизнес-приложения, включая приложение корпоративного портала, на устройствах Windows 8.1 Desktop или Windows 10 Desktop и Windows 10 Mobile. Чтобы развернуть приложения APPX на устройствах Windows 8.1 Desktop или Windows 10 Desktop и Windows 10 Mobile, можно использовать сертификат подписи кода из общедоступного центра сертификации, которому уже доверяют ваши устройства Windows, либо вы можете использовать собственный центр сертификации.

 > [!NOTE]
 > Для Windows 8.1 Desktop требуется разрешение на загрузку неопубликованного приложения в рамках корпоративной политики либо использование ключей загрузки неопубликованного приложения (автоматически включено для присоединенных к домену устройств). Дополнительные сведения о загрузке неопубликованного приложения Windows 8 см. [здесь](https://blogs.technet.microsoft.com/scd-odtsp/2012/09/27/windows-8-sideloading-requirements-from-technet/).

## <a name="windows-10-sideloading"></a>Загрузка неопубликованного приложения в Windows 10

В Windows 10 загрузка неопубликованного приложения отличается от загрузки в предшествующих версиях Windows:

- Разблокировать устройство для загрузки неопубликованного приложения можно с помощью корпоративной политики. Intune предоставляет политику конфигурации устройств с именем "Установка доверенного приложения". Задать для нее значение <allow> — это все, что необходимо для устройств, которые уже доверяют сертификату, используемому для подписания приложения APPX.

- Сертификаты Symantec Phone и ключи лицензии на загрузку неопубликованных приложений не требуются. Но если локальный центр сертификации недоступен, может потребоваться получить сертификат подписи кода из общедоступного центра сертификации. Дополнительные сведения см. в разделе [Introduction to Code Signing](https://docs.microsoft.com/windows/desktop/SecCrypto/cryptography-tools#introduction-to-code-signing) (Общие сведения о подписывании кода).

### <a name="code-sign-your-app"></a>Подписывание приложения

Первый шаг — это подписание пакета APPX. Дополнительные сведения см. в статье [Sign an app package using SignTool](https://docs.microsoft.com/windows/uwp/packaging/sign-app-package-using-signtool) (Подписание пакета приложения с помощью SignTool).

### <a name="upload-your-app"></a>Отправка приложения

Затем необходимо передать подписанный APPX-файл. Дополнительные сведения см. в статье [Сведения о добавлении бизнес-приложения Windows в Microsoft Intune](lob-apps-windows.md).

Если приложение развертывается в соответствии с требованиями пользователей или устройств, приложение Корпоративного портала Intune не требуется. Но если приложение развертывается как доступное для пользователей, они могут использовать приложение корпоративного портала из общедоступного магазина Microsoft Store, использовать приложение корпоративного портала из частного магазина Microsoft Store для бизнеса либо подписать и вручную развернуть приложение Корпоративного портала Intune.

### <a name="upload-the-code-signing-certificate"></a>Отправка сертификата подписи кода

Если устройство Windows 10 еще не доверяет центру сертификации, после подписи пакета APPX и его отправки в службу Intune необходимо передать сертификат подписи кода на портал Intune:
1. Щелкните "Клиентские приложения".
2. Щелкните "Сертификаты Windows Корпоративная".
3. Выберите "Выбрать файл" в разделе сертификата подписи кода.
4. Выберите CER-файл и нажмите кнопку "Отправить".

Теперь любое устройство Windows 10 Desktop и Windows 10 Mobile с развертыванием APPX в службе Intune будет автоматически скачивать соответствующий корпоративный сертификат и приложению будет разрешено выполнять запуск после установки.

Intune развертывает только последний отправленный CER-файл. Если у вас есть несколько файлов APPX, созданных разными разработчиками, не связанными с вашей организацией, вам потребуется попросить их предоставить неподписанные файлы APPX для подписи с помощью вашего сертификата либо предоставить им сертификат подписи кода, который использует ваша организация.

## <a name="how-to-renew-the-symantec-enterprise-code-signing-certificate"></a>Инструкции по обновлению корпоративного сертификата Symantec для подписи кода

Поддержка сертификата, используемого для развертывания мобильных приложений Windows Phone 8,1, была прекращена 28 февраля 2019 года и больше не доступна для продления от Symantec. При развертывании в Windows 10 Mobile можно продолжать использовать сертификаты подписи кода Symantec Desktop Enterprise, выполнив инструкции в статье [Загрузка неопубликованного приложения в Windows 10](app-sideload-windows.md#windows-10-sideloading).

## <a name="how-to-install-the-updated-certificate-for-line-of-business-lob-apps"></a>Установка обновленного сертификата для бизнес-приложений

Windows Phone 8.1

Служба Intune не может развертывать бизнес-приложения для этой платформы после истечения срока действия имеющегося сертификата подписи кода Symantec Mobile Enterprise. По-прежнему можно будет загружать неопубликованные неподписанные файлы XAP/APPX с помощью SD-карты или путем скачивания файла на устройство. Дополнительные сведения см. в разделе [How to install XAP files on Windows Phone](https://answers.microsoft.com/en-us/mobiledevices/forum/mdlumia-mdapps/how-to-install-xap-file-in-windows-phone-8/da09ee72-51ae-407c-9b85-bc148df89280) (Практическое руководство. Установка XAP-файлов на Windows Phone).

Windows 8.1 Desktop или Windows 10 Desktop и Windows 10 Mobile

Если срок действия сертификата истек, возможно, файлы APPX не будут запускаться. Вы должны получить новый CER-файл и выполнить инструкции по подписанию каждого развернутого файла APPX и повторно отправить все файлы APPX и обновленный CER-файл в раздел "Сертификаты Windows Корпоративная" на портале Intune.

## <a name="manually-deploy-windows-10-company-portal-app"></a>Развертывание приложения корпоративного портала для Windows 10 вручную
Если вы не хотите предоставлять доступ к Microsoft Store, приложение корпоративного портала для Windows 10 можно развернуть вручную напрямую из Intune, даже если служба Intune еще не интегрирована с Microsoft Store для бизнеса (MSFB). Кроме того, если интеграция выполнена, можно развернуть приложение корпоративного портала, следуя инструкциям из [этой статьи](store-apps-windows.md).

 > [!NOTE]
 > В этом случае при появлении каждого обновления приложения его будет необходимо развертывать вручную.

1. Войдите в свою учетную запись в [Microsoft Store для бизнеса](https://www.microsoft.com/business-store) и получите версию **автономной лицензии** для приложения корпоративного портала.  
2. После получения приложения выберите его на странице **Инвентаризация**.  
3. Выберите **Все устройства Windows 10** в разделе **Платформа**, затем соответствующую **архитектуру** и скачиваемый файл. Для этого приложения файл лицензии не требуется.
   ![Изображение со сведениями о пакете Windows 10 (X86), доступном для скачивания](./media/app-sideload-windows/Win10CP-all-devices.png)
4. Скачайте все пакеты в группе "Необходимые платформы". Это необходимо сделать для архитектур x86, x64 и ARM — всего 9 пакетов, как показано ниже.

   ![Изображение файлов зависимостей для скачивания ](./media/app-sideload-windows/Win10CP-dependent-files.png)
5. Перед отправкой приложения корпоративного портала в Intune создайте папку (например, C:&#92;Company Portal) с пакетами и структурируйте их следующим образом.
   1. Поместите пакет корпоративного портала в папку C:\Company Portal. Создайте в этой папке подпапку "Dependencies" (Зависимости).  
      ![Изображение сохраненной папки "Dependencies" с APPXBUN-файлом](./media/app-sideload-windows/Win10CP-Dependencies-save.png)
   2. Поместите девять пакетов зависимостей в папку "Dependencies".  
      Если пакеты зависимостей помещены в папку по-другому, Intune не сможет их распознать и отправить их при отправке пакетов, в результате чего произойдет следующая ошибка отправки.  
      ![Сообщение об ошибке, в котором сообщается, что нужно указать зависимость приложений Windows.](./media/app-sideload-windows/Win10CP-error-message.png)
6. Вернитесь в Intune и отправьте приложение корпоративного портала как новое приложение. Разверните его как обязательное приложение для требуемой группы целевых пользователей.  

Дополнительные сведения об обработке зависимостей для универсальных приложений в Intune см. в разделе [Развертывание appxbundle с зависимостями через Microsoft Intune MDM](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/).  

### <a name="how-do-i-update-the-company-portal-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>Как обновить корпоративный портал на устройствах моих пользователей, если они уже установили старые приложения из магазина?
Если пользователи уже установили из магазина приложения корпоративного портала для Windows 8.1 или Windows Phone 8.1, то у них должно быть автоматически выполнено обновление до новой версии (никаких дополнительных действий ни вам, ни вашим пользователям выполнять не нужно). Если обновление не происходит, попросите пользователей проверить, включена ли на их устройствах функция автоматического обновления для приложений из Магазина.   

### <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Как обновить мое загруженное неопубликованное приложение корпоративного портала для Windows 8.1 до приложения корпоративного портала для Windows 10?
Для миграции рекомендуем удалить развернутое приложение корпоративного портала для Windows 8.1. В этом случае выберите для действия развертывания значение "Удалить". После этого приложение корпоративного портала для Windows 10 можно будет развернуть с помощью любого из перечисленных выше способов.  

Если нужно загрузить неопубликованное приложение, и вы развернули корпоративный портал для Windows 8.1 без подписи с помощью сертификата Symantec, выполните для обновления процедуру развертывания непосредственно через Intune, описанную выше.

Если нужно загрузить неопубликованное приложение, и вы подписали и развернули корпоративный портал для Windows 8.1 с помощью сертификата подписи кода Symantec, выполните процедуру, описанную ниже.  

### <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Как обновить мое подписанное и загруженное неопубликованное приложение корпоративного портала для Windows Phone 8.1 или приложение корпоративного портала для Windows 8.1 до приложения корпоративного портала для Windows 10?
Для миграции рекомендуем удалить развернутое приложение корпоративного портала для Windows Phone 8.1 или Windows 8.1. В этом случае выберите для действия развертывания значение "Удалить". После этого приложение корпоративного портала для Windows 10 можно будет развернуть обычным образом.  

В противном случае приложение корпоративного портала для Windows 10 необходимо соответствующим образом обновить и подписать, чтобы соблюсти нужный путь обновления.  

Если приложение корпоративного портала для Windows 10 подписано и развернуто таким способом, эту процедуру необходимо будет повторить для каждого нового обновления приложения, когда оно появится в магазине. При обновлении в магазине приложения не будут обновляться автоматически.  

Ниже рассмотрена процедура подписания и развертывания приложения.

1. Скачайте скрипт подписывания приложения корпоративного портала для Microsoft Intune Windows 10 со страницы [https://aka.ms/win10cpscript](https://aka.ms/win10cpscript).  Для этого скрипта необходимо, чтобы на главном компьютере был установлен пакет Windows SDK для Windows 10. Чтобы скачать пакет SDK для Windows 10, посетите веб-сайт [https://go.microsoft.com/fwlink/?LinkId=619296](https://go.microsoft.com/fwlink/?LinkId=619296).
2. Скачайте приложение корпоративного портала для Windows 10 из Магазина Майкрософт для бизнеса, как описано выше.  
3. Запустите скрипт с входными параметрами, подробно описанными в заголовке скрипта, чтобы подписать приложение корпоративного портала для Windows 10 (см. пример ниже). Зависимости не обязательно передавать в скрипт. Они будут нужны только в том случае, если приложение отправляется в консоль администрирования Intune.

|       Параметр       |                                                                    Описание                                                                    |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| InputWin10AppxBundle  |                                             Путь к исходному файлу appxbundle.                                              |
| OutputWin10AppxBundle |                                                  Выходной путь для подписанного файла appxbundle.                                                  |
|       Win81Appx       |                          Путь к файлу (APPX) корпоративного портала для Windows 8.1 или Windows Phone 8.1.                           |
|      PfxFilePath      |                                   Путь к файлу (.PFX) корпоративного сертификата подписи кода для мобильных устройств Symantec.                                    |
|      PfxPassword      |                                     Пароль корпоративного сертификата подписи кода для мобильных устройств Symantec.                                      |
|      PublisherId      |      Идентификатор издателя организации. Если он отсутствует, используется поле Subject (Тема) корпоративного сертификата подписи кода для мобильных устройств Symantec.       |
|        SdkPath        | Путь к корневой папке пакета Windows SDK для Windows 10. Этот аргумент является необязательным и по умолчанию имеет значение ${env:ProgramFiles(x86)}\Windows Kits\10 |

По окончании работы скрипт создаст подписанную версию приложения корпоративного портала для Windows 10. Затем подписанную версию приложения можно будет развернуть как бизнес-приложение через Intune, что приведет к обновлению развернутых сейчас версий до этого нового приложения.  