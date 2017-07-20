---
title: "Управление веб-доступом с помощью приложения Managed Browser"
titleSuffix: Intune on Azure
description: "Сведения о развертывании приложения Managed Browser для ограничения просмотра веб-страниц и передачи веб-данных в другие приложения.\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1feca24f-9212-4d5d-afa9-7c171c5e8525
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e85306934b68f64bad8c223ac117190607db8473
ms.sourcegitcommit: fd5b7aa26446d2fa92c21638cb29371e43fe169f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2017
---
# <a name="manage-internet-access-using-managed-browser-policies-with-microsoft-intune"></a>Управление доступом в Интернет с помощью политик Managed Browser в Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Managed Browser — это корпоративное приложение для просмотра веб-страниц, которое можно скачать из общедоступных магазинов приложений. При настройке с помощью Intune:
- Managed Browser можно использовать для защищенного доступа к корпоративным сайтам и приложениям на основе модели SaaS с единым входом через службу MyApps;
- в Managed Browser можно предварительно настроить список URL-адресов и доменов, чтобы ограничить набор сайтов, доступных пользователям в контексте организации.
- для Managed Browser можно предварительно настроить заданные закладки и домашнюю страницу.

Так как это приложение можно интегрировать с пакетом SDK для Intune, к нему также можно применить политики защиты приложений, включая следующее:
- контроль за использованием операций вырезания, копирования и вставки;
- предотвращение создания снимков экрана;
- обеспечение того, чтобы выбираемые пользователями ссылки на содержимое открывались только в других управляемых приложениях.

Дополнительные сведения см. в разделе [Что такое политики защиты приложений?](/intune/app-protection-policy).

Эти параметры могут применяться к устройствам, зарегистрированным в службе Intune или другом решении для управления устройствами, а также к устройствам, которые не находятся под управлением.

Приложение Managed Browser, которое установлено пользователем из магазина и не находится под управлением Intune, можно использовать в качестве обычного браузера, поддерживающего функцию единого входа через сайт Microsoft MyApps. В этом случае пользователи перенаправляются на сайт MyApps, где им предлагается подготовленный список SaaS-приложений.
Если Managed Browser не находится под управлением Intune, его нельзя использовать для доступа к данным других управляемых в Intune приложений. 

Managed Browser не поддерживает протокол шифрования SSL версии 3 (SSLv3).

Политики Managed Browser можно создать для следующих типов устройств:

-   Устройства под управлением Android 4 и более поздней версии.

-   Устройства под управлением iOS 8.0 и более поздней версии.

Intune Managed Browser поддерживает открытие веб-контента из [приложений партнеров Microsoft Intune](https://www.microsoft.com/server-cloud/products/microsoft-intune/partners.aspx).

## <a name="create-a-managed-browser-app-configuration"></a>Создание конфигурации приложения Managed Browser

1.  Зарегистрируйтесь на портале Azure.
2.  Выберите **Больше служб** > **Мониторинг и управление** > **Intune**.
3.  В колонке **Мобильные приложения** списка "Управление" выберите **Политики конфигурации приложений**.
4.  В колонке **Политики конфигурации приложений** выберите **Добавить**.
5.  В колонке **Добавить конфигурацию приложения** введите значения в поля **Имя** и, при необходимости, **Описание** для параметров конфигурации приложения.
6.  Для типа **Регистрация устройства** выберите **Не зарегистрировано в Intune**.
7.  Выделите **Выбрать необходимые приложения**. Затем в колонке **Целевые приложения** выберите **Managed Browser** для iOS, Android или одновременно обеих платформ.
8.  Нажмите кнопку **ОК** для возврата к колонке **Добавить конфигурацию приложения**.
9.  Выберите **Параметры конфигурации** . В колонке **Конфигурация** можно определить пары ключей и значений, которые будут задавать конфигурацию Managed Browser. Сведения о доступных парах ключей и значений см. далее в этой статье.
10. По завершении нажмите кнопку **ОК**.
11. В колонке **Добавить конфигурацию приложения** выберите **Создать**.
12. Созданная конфигурация отображается в колонке **Конфигурация приложения**.

>[!IMPORTANT]
>Сейчас в Managed Browser используется автоматическая регистрация. Чтобы применить конфигурацию приложения, на устройстве должно уже присутствовать другое приложение, управляемое политиками защиты приложений Intune.

## <a name="assign-the-configuration-settings-you-created"></a>Назначение созданных параметров конфигурации

Эти параметры назначаются группам пользователей Azure AD. Если у пользователя установлено приложение Managed Browser, оно управляется в соответствии с заданными параметрами.

1. В колонке **Параметры** на панели мониторинга для управления мобильными приложениями Intune выберите **Конфигурация приложения**.
2. В списке конфигураций приложений выберите ту, которую требуется назначить.
3. В следующей колонке выберите **Группы пользователей**.
4. В колонке **Группы пользователей** выберите группу Azure AD, которой требуется назначить конфигурацию приложения, после чего нажмите кнопку **ОК**.


## <a name="how-to-configure-application-proxy-settings-for-the-managed-browser"></a>Настройка параметров прокси приложения для Managed Browser

Intune Managed Browser и [прокси приложения Azure AD]( https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) можно использовать совместно, чтобы обеспечить поддержку следующих сценариев для пользователей устройств iOS и Android.

- Пользователь скачивает приложение Microsoft Outlook и входит в него.  Автоматически применяются политики защиты приложений Intune. Они шифруют сохраненные данные и не позволяют пользователю передавать корпоративные файлы в неуправляемые приложения или расположения на устройстве. Когда пользователь открывает ссылку на сайт интрасети в Outlook, вы можете указать, чтобы она открывалась в приложении Managed Browser, а не другом браузере.
Managed Browser распознает, что этот сайт интрасети был предоставлен пользователю с помощью прокси приложения. Пользователь автоматически перенаправляется через прокси приложения для проверки подлинности с использованием любой применимой многофакторной проверки подлинности и функций условного доступа, прежде чем перейти на сайт интрасети. Этот сайт, который ранее мог быть не найден, так как пользователь работал удаленно, теперь доступен, и ссылка в Outlook работает должным образом.  

- Удаленный пользователь открывает приложение Managed Browser и переходит на сайт интрасети по внутреннему URL-адресу. Managed Browser распознает, что этот сайт интрасети был предоставлен пользователю с помощью прокси приложения. Пользователь автоматически перенаправляется через прокси приложения для проверки подлинности с использованием любой применимой многофакторной проверки подлинности и функций условного доступа, прежде чем перейти на сайт интрасети.
Этот сайт, который ранее мог быть не найден, так как пользователь работал удаленно, теперь доступен.  

### <a name="before-you-start"></a>Перед началом работы

- Убедитесь, что внутренние приложения опубликованы через прокси приложения Azure AD.
- Чтобы настроить прокси приложения и опубликовать приложения, см. [документацию по установке]( https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started#how-to-get-started). 
- Версия используемого приложения Managed Browser должна быть 1.2.0 или выше.
- Приложению Managed Browser у пользователей должна быть назначена [политика защиты приложений Intune]( app-protection-policy.md).
- Пользователи могут просматривать автоматическое перенаправление только для назначенных им приложений прокси приложения.

#### <a name="step-1-enable-automatic-redirection-to-the-managed-browser-from-outlook"></a>Шаг 1. Включение автоматического перенаправления в Managed Browser из Outlook
Для Outlook должна быть настроена политика защиты приложений с включенным параметром **Ограничить веб-контент, отображаемый в Managed Browser**.

#### <a name="step-2-assign-an-app-configuration-policy-assigned-for-the-managed-browser"></a>Шаг 2. Назначение политики конфигурации приложений, назначенной для приложения Managed Browser
Эта процедура позволяет настроить приложение Managed Browser для использования перенаправления прокси приложения. При создании конфигурации приложения Managed укажите следующие пары ключей и значений:

|||
|-|-|
|Key|Значение|
|**com.microsoft.intune.mam.managedbrowser.AppProxyRedirection**|**true**|


## <a name="how-to-configure-the-homepage-for-the-managed-browser"></a>Настройка домашней страницы для Managed Browser

Этот параметр позволяет настроить домашнюю страницу, которую видят пользователи при запуске Managed Browser или открытии новой вкладки. При создании конфигурации приложения Managed укажите следующие пары ключей и значений:

|||
|-|-|
|Key|Значение|
|**com.microsoft.intune.mam.managedbrowser.homepage**|Укажите допустимый URL-адрес. Неправильные URL-адреса блокируются из соображений безопасности.<br>Пример: **https://www.bing.com**.|


## <a name="how-to-configure-bookmarks-for-the-managed-browser"></a>Настройка закладок для Managed Browser

Этот параметр позволяет настроить набор закладок, доступных пользователям Managed Browser.

- Пользователи не могут изменить или удалить эти закладки.
- Эти закладки отображаются в начале списка. Все создаваемые пользователями закладки отображаются под ними.

При создании конфигурации приложения Managed укажите следующие пары ключей и значений:

|||
|-|-|
|Key|Значение|
|**com.microsoft.intune.mam.managedbrowser.bookmarks**|Значением для этой конфигурации является список закладок. Каждая закладка состоит из заголовка и URL-адреса. Для разделения заголовка и URL-адреса используется символ **&#124;**.<br><br>Пример: **Microsoft Bing&#124;https://www.bing.com**<br><br>Чтобы настроить несколько закладок, разделите каждую пару двойным символом — **&#124;&#124;**.<br><br>Пример: **Bing&#124;https://www.bing.com&#124;&#124;Contoso&#124;https://www.contoso.com**|

## <a name="how-to-specify-allowed-and-blocked-urls-for-the-managed-browser"></a>Настройка списков разрешенных и запрещенных URL-адресов для Managed Browser

При создании конфигурации приложения Managed укажите следующие пары ключей и значений:

|||
|-|-|
|Key|Значение|
|Выберите один из следующих типов.<br><br>— Укажите разрешенные URL-адреса (остальные сайты будут недоступны): **com.microsoft.intune.mam.managedbrowser.AllowListURLs**.<br><br>— Укажите заблокированные URL-адреса (все остальные сайты будут доступны): <br><br>**com.microsoft.intune.mam.managedbrowser.BlockListURLs**.|В качестве значения, соответствующего ключу, указывается список URL-адресов. Введите все URL-адреса, которые требуется разрешить или заблокировать, в виде одного значения, разделяя их символом вертикальной черты **&#124;**.<br><br>Примеры:<br><br>-**URL1&#124;URL2&#124;URL3**<br>-**http://*.contoso.com/*&#124;https://*.bing.com/*&#124;https://expenses.contoso.com**|

>[!IMPORTANT]
>Не указывайте оба ключа одновременно. Если для одного пользователя заданы оба ключа, используется разрешающий ключ, который накладывает более строгие ограничения.
>Кроме того, убедитесь, что вы не заблокировали важные страницы, например веб-сайты своей организации.

### <a name="url-format-for-allowed-and-blocked-urls"></a>Формат для разрешенных и заблокированных URL-адресов
Ниже приведены сведения о допустимых форматах и подстановочных знаках, которые можно использовать при указании URL-адресов в списках разрешений и блокировок.

-   Вы можете использовать подстановочный знак **&#42;** в соответствии со следующим списком разрешенных шаблонов.

-   Убедитесь, что для всех вводимых в список URL-адресов используется префикс **http** или **https** .

-   В адресе можно указать номера портов. Если не указать номер порта, используются следующие значения.

    -   Порт 80 для http

    -   Порт 443 для https

    Использование подстановочных знаков в номерах портов не поддерживается. Например, варианты вида **http&colon;//www&period;contoso&period;com:*;** и **http&colon;//www&period;contoso&period;com: /*;** не поддерживаются.

-   В следующей таблице приведены сведения о шаблонах, которые можно использовать при указании URL-адресов.

|URL-адрес|Подробные сведения|Соответствует|Не соответствует|
    |-------|---------------|-----------|------------------|
    |http://www.contoso.com|Соответствует отдельной странице|www.contoso.com|host.contoso.com<br /><br />www.contoso.com/images<br /><br />contoso.com/|
    |http://contoso.com|Соответствует отдельной странице|contoso.com/|host.contoso.com<br /><br />www.contoso.com/images<br /><br />www.contoso.com|
    |http://www.contoso.com/&#42;|Соответствует всем URL-адресам, которые начинаются с www.contoso.com|www.contoso.com<br /><br />www.contoso.com/images<br /><br />www.contoso.com/videos/tvshows|host.contoso.com<br /><br />host.contoso.com/images|
    |http://&#42;.contoso.com/&#42;|Соответствует всем поддоменам в contoso.com|developer.contoso.com/resources<br /><br />news.contoso.com/images<br /><br />news.contoso.com/videos|contoso.host.com|
    |http://www.contoso.com/images|Соответствует отдельной папке|www.contoso.com/images|www.contoso.com/images/dogs|
    |http://www.contoso.com:80|Соответствует отдельной странице с использованием номера порта|http://www.contoso.com:80|
    |https://www.contoso.com|Соответствует отдельной защищенной странице|https://www.contoso.com|http://www.contoso.com|
    |http://www.contoso.com/images/&#42;|Соответствует отдельной папке и всем вложенным в нее папкам|www.contoso.com/images/dogs<br /><br />www.contoso.com/images/cats|www.contoso.com/videos|

-   Ниже приведены примеры входных данных, которые не следует указать:

    -   &#42;.com

    -   &#42;.contoso/&#42;

    -   www.contoso.com/&#42;images

    -   www.contoso.com/&#42;images&#42;pigs

    -   www.contoso.com/page&#42;

    -   IP-адреса

    -   https://&#42;

    -   http://&#42;

    -   http://www.contoso.com:&#42;

    -   http://www.contoso.com: /&#42;

## <a name="security-and-privacy-for-the-managed-browser"></a>Обеспечение безопасности и конфиденциальности Managed Browser

-   На устройствах с iOS пользователям нельзя открывать веб-сайты, сертификат которых имеет истекший срок действия или не является доверенным.

-   В Managed Browser не будут применяться параметры, настроенные пользователями для встроенного браузера на их устройствах. Managed Browser не имеет доступа к этим параметрам.

-   Если вы настраиваете параметры **Требовать простой ПИН-код для доступа** или **Требовать для доступа учетные данные организации** в политике защиты приложений, сопоставленной с Managed Browser, и пользователь открывает ссылку на справку на странице проверки подлинности, он сможет просматривать все веб-сайты независимо от того, были ли они добавлены в список блокировок в этой политике.

-   Managed Browser может заблокировать доступ к сайтам только в том случае, если доступ к ним осуществляется напрямую. Он не блокирует доступ при использовании промежуточных служб (например, службы перевода) для доступа к сайту.

-   Для проверки подлинности и доступа к документации Intune домен **&#42;.microsoft.com** исключается из списков разрешений или блокировки. — он разрешен всегда.

### <a name="turn-off-usage-data"></a>Отключение данных об использовании
Корпорация Майкрософт автоматически собирает анонимные данные о производительности и использовании Managed Browser для усовершенствования продуктов и служб Майкрософт. Пользователи могут отключить сбор данных с помощью параметра **Данные об использовании** на устройствах. У вас нет контроля за сбором этих данных.

