---
title: Устранение неполадок управления мобильными приложениями
titleSuffix: Microsoft Intune
description: В этой статье описаны некоторые советы по устранению неполадок с развертыванием политик условного доступа.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/03/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: cd5a0a3b-0013-4be3-a233-ce6e9083149f
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 43fd8207a07f64fd293eb9c90bbfc2a8dadd9157
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72489932"
---
# <a name="troubleshoot-mobile-application-management"></a>Устранение неполадок управления мобильными приложениями

В этом разделе приводятся решения распространенных проблем, возникающих при использовании Защита приложений Intune (также называемых MAM или управлением мобильными приложениями).

Если эти сведения не позволяют решить проблему, см. дополнительные справочные материалы в статье [Получение поддержки для Microsoft Intune](../fundamentals/get-support.md).

## <a name="common-it-administrator-issues"></a>Проблемы, с которыми часто сталкивается ИТ-администратор

Это распространенные проблемы, с которыми ИТ-администратор может столкнуться при работе с политиками защиты приложений Intune.

| Проблема | Описание | Решение |
| -- | -- | -- |
| Политика не применяется к Skype для бизнеса | Политика защиты приложений без регистрации устройств, созданная на портале Azure, не применяется к приложению Skype для бизнеса на устройствах iOS и Android. | В Skype для бизнеса следует настроить современную проверку подлинности.  Следуйте инструкциям, приведенным в статье, посвященной [включению современной проверки подлинности для клиента](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx), чтобы настроить современную проверку подлинности для Skype. |
| Не применяется политика для приложений Office | Политики защиты приложения не применяются ни к одному из [поддерживаемых приложений Office](https://www.microsoft.com/cloud-platform/microsoft-intune-partners) для любого пользователя. | Убедитесь, что у пользователя есть лицензия для Intune, а развернутая политика защиты приложений нацелена на приложения Office. Для применения вновь развернутой политики защиты приложений может потребоваться до 8 часов. |
| Администратору не удается настроить политику защиты приложений на портале Azure | ИТ-администратору не удается настроить политики защиты приложений на портале Azure. | Следующие роли пользователей имеют доступ к порталу Azure: <ul><li>глобальный администратор, учетную запись которого можно настроить в [центре администрирования Microsoft 365](https://admin.microsoft.com/);</li><li>владелец, учетную запись которого можно настроить на [портале Azure](https://portal.azure.com/);</li><li>участник, учетную запись которого можно настроить на [портале Azure](https://portal.azure.com/).</li></ul> Сведения о настройке этих ролей см. в статье [Управление доступом на основе ролей (RBAC) с помощью Microsoft Intune](../fundamentals/role-based-access-control.md).|
|Учетные записи пользователей отсутствуют в отчетах о политиках защиты приложений | Отчеты консоли администратора не показывают учетные записи пользователей, для которых недавно была развернута политика защиты приложений. | Если пользователь недавно добавлен в политику защиты приложений, отображение этого пользователя в отчетах как целевого может занять до 24 часов. |
| Изменения политики не работают | Применение изменений и обновлений политики защиты приложений может занять до 8 часов. | При необходимости конечный пользователь может выйти из приложения и повторить вход для принудительной синхронизации со службой. |
| Политика защиты приложений не работает с DEP | Политика защиты приложений не применяется к устройствам Apple DEP. | Убедитесь, что вы используете сопоставление пользователей в рамках программы регистрации устройств (DEP) Apple. Сопоставление пользователей необходимо для всех приложений, требующих проверку подлинности пользователей в рамках DEP. <br><br>Дополнительные сведения о регистрации устройств iOS в рамках программы DEP см. в статье [Автоматическая регистрация устройств iOS с помощью Программы регистрации устройств Apple](../enrollment/device-enrollment-program-enroll-ios.md).|
| Политика передачи данных не работает с iOS | Политики **Разрешить приложению передавать данные другим приложениям** и **Разрешить приложению принимать данные от других приложений** не позволяют успешно управлять передачей данных в iOS. | См. статью [Как управлять передачей данных между приложениями iOS в Microsoft Intune](data-transfer-between-apps-manage-ios.md). |

## <a name="common-end-user-issues"></a>Распространенные проблемы конечных пользователей

Распространенные проблемы конечных пользователей разделены на следующие категории:

* **Сценарии обычного использования**. Конечный пользователь может столкнуться с этими сценариями в приложениях, имеющих политику защиты приложений Intune. Эти проблемы не являются критическими, однако могут восприниматься как ошибки.

* **Диалоговые окна обычного использования**. Конечный пользователь может столкнуться с этими диалоговыми окнами в приложениях, имеющих политику защиты приложений Intune. Эти сообщения и диалоговые окна **не** указывают ошибку.

* **Сообщения об ошибках и диалоговые окна с ошибками**. Конечный пользователь может столкнуться с этими сообщениями и диалоговыми окнами в приложениях, имеющих политику защиты приложений Intune. Они часто указывают на то, что ИТ-администратор допустил ошибку, либо на проблему с функцией защиты приложений Intune.

### <a name="normal-usage-scenarios"></a>Сценарии обычного использования

Платформа | Сценарий | Описание |
---| --- | --- |
iOS | Пользователь может использовать расширение для общего доступа iOS, чтобы открывать рабочие или учебные данные в неуправляемых приложениях, даже если политика передачи данных установлена в значение **Managed apps only** (Только управляемые приложения ) или **No apps** (Никакие приложения). Не приведет ли это к утечке данных? | С помощью политики защиты приложений Intune нельзя управлять расширением для общего доступа iOS, не управляя самим устройством. Следовательно, **Intune зашифровывает корпоративные данные, прежде чем использовать их за пределами приложения**. Это можно проверить, попытавшись открыть корпоративный файл за пределами управляемого приложения. Такой файл должен быть зашифрован, и его не удастся открыть за пределами управляемого приложения.
iOS | Почему конечным пользователям **предлагается установить приложение Microsoft Authenticator** | Это необходимо, если применяется условный доступ на основе приложений. см. статью [требование утвержденного клиентского приложения](https://docs.microsoft.com/azure/active-directory/conditional-access/app-based-conditional-access).
Android | Почему конечному пользователю **нужно установить приложение корпоративного портала**, даже если используется защита приложений MAM без регистрации устройства?  | В Android большинство функций защиты приложений встроены в приложение корпоративного портала. **И хотя приложение корпоративного портала требуется всегда, регистрация устройств не обязательна**. Для использования защиты приложений без регистрации на пользовательском устройстве должно быть установлено приложение корпоративного портала.
iOS/Android | Политика защиты приложений не применяется к черновику электронной почты в приложении Outlook | Так как Outlook поддерживает как корпоративный, так и личный контекст, он не применяет MAM к черновику электронной почты.
iOS/Android | Политика защиты приложений не применяется к новым документам в WXP (Word, Excel, PowerPoint) | Так как WXP поддерживает как корпоративный, так и личный контекст, он не применяет MAM к новым документам, пока они не будут сохранены в определенном корпоративном расположении, например в OneDrive.
iOS/Android | Приложения, не разрешающие сохранение в локальном хранилище, если включена политика | Поведение приложения для этого параметра управляется разработчиком приложения.
Android | У Android есть больше ограничений, чем iOS, в которых "собственные" приложения могут получать доступ к содержимому, защищенному MAM | Android — это открытая платформа, и "собственное" Сопоставление приложения может быть изменено конечным пользователем для потенциально небезопасных приложений. Применение [исключений политики обмена данными](app-protection-policies-exception.md) для исключения определенных приложений.
Android | Azure Information Protection (точка административной установки) может сохранить файл PDF, если запрещено сохранение как | Если используется параметр "отключить печать" при использовании параметра "Сохранить как PDF", точка административного сохранения учитывает политику MAM.
iOS | Открытие вложений PDF в приложении Outlook завершается с ошибкой "действие не разрешено | Это может произойти, если пользователь не прошел проверку подлинности в Acrobat Reader для Intune или использовал отпечаток для проверки подлинности в Организации. Предварительно откройте программу Acrobat Reader и выполните проверку подлинности с помощью учетных данных UPN.


### <a name="normal-usage-dialogs"></a>Диалоговые окна обычного использования

Платформа | Сообщение или диалоговое окно | Описание |
--- | --- | --- |
iOS, Android | **Вход**: для защиты данных вашей организации нужно управлять этим приложением. Чтобы выполнить это действие, войдите с помощью рабочей или учебной учетной записи. | Чтобы использовать это приложение, пользователь должен войти с помощью рабочей или учебной учетной записи, для чего требуется политика защиты приложений. Чтобы применить политику, пользователю нужно пройти проверку подлинности в Azure Active Directory.
iOS, Android |**Требуется перезапуск**: ваша организация теперь защищает свои данные в этом приложении. Чтобы продолжить работу, нужно перезапустить приложение. | Для приложения только что была настроена политика защиты приложений Intune, и его нужно перезапустить для применения политики.
iOS, Android |**Действие запрещено**: организация разрешает открывать только рабочие или учебные данные в этом приложении. | ИТ-администратор установил для параметра **Разрешить приложению принимать данные от других приложений** значение **Только управляемые приложения**. Таким образом, пользователь может передать данные в это приложение только из других приложений, использующих политику защиты приложений.
iOS, Android |**Действие запрещено**: ваша организация разрешает передавать данные только в другие управляемые приложения. | ИТ-администратор установил для параметра **Разрешить приложению передавать данные другим приложениям** значение **Только управляемые приложения**. Таким образом, пользователь может передать данные из этого приложения только в приложения, использующие политику защиты приложений.
iOS, Android |**Оповещение об очистке**: данные, связанные с этим приложением, были удалены организацией. Чтобы продолжить, перезапустите приложение. | ИТ-администратор запустил очистку приложения с помощью функции защиты приложений Intune.
Android | **Company Portal required** (Требуется корпоративный портал): чтобы использовать рабочую или учебную учетную запись с этим приложением, нужно установить приложение корпоративного портала Intune. Нажмите кнопку "Перейти в магазин", чтобы продолжить. | В Android большинство функций защиты приложений встроены в приложение корпоративного портала. **И хотя приложение корпоративного портала требуется всегда, регистрация устройств не обязательна**. Для использования защиты приложений без регистрации на пользовательском устройстве должно быть установлено приложение корпоративного портала.

### <a name="error-messages-and-dialogs-on-ios"></a>Сообщения об ошибках и диалоговые окна с ошибками в iOS

Сообщение об ошибке или диалоговое окно | Причина | Серверы |
-- | --- | --- |
**Приложение не настроено**: это приложение не настроено для использования. Для получения дополнительных сведений обратитесь к ИТ-администратору. | Не удалось обнаружить требуемую политику защиты для приложения. |Убедитесь, что политика защиты приложений iOS развернута для группы безопасности пользователя и нацелена на это приложение.
**Управляемый Intune браузер**: это приложение лучше всего работает, если управляется Microsoft Intune. Его всегда можно использовать для просмотра веб-страниц, а если оно управляется Microsoft Intune, вы получите доступ к дополнительным функциям защиты данных. | Не удалось обнаружить необходимую политику защиты приложений для приложения Intune Managed Browser. <br><br>Пользователь по-прежнему может использовать это приложение для просмотра веб-страниц, однако оно не управляется Intune. | Убедитесь, что политика защиты приложений iOS развернута для группы безопасности пользователя и нацелена на приложение Intune Managed Browser.
**Не удалось войти в систему**: сейчас вход в систему невозможен. Повторите попытку позже. | Сбой при регистрации пользователя с использованием службы MAM после того, как пользователь пытается войти в систему с помощью своей рабочей или учебной учетной записи. | Убедитесь, что политика защиты приложений iOS развернута для группы безопасности пользователя и нацелена на это приложение.
**Учетная запись не настроена**: организация не настроила для вашей учетной записи доступ к рабочим или учебным данным. За помощью обратитесь к ИТ-администратору. | У учетной записи пользователя нет лицензии Intune A Direct. | Убедитесь, что на [портале администрирования Microsoft 365](https://admin.microsoft.com) учетной записи пользователя назначена лицензия Intune.
**Устройство не соответствует требованиям**: это приложение невозможно использовать, так как на устройстве снято ограничение на доступ к файловой системе. Для получения дополнительных сведений обратитесь к ИТ-администратору. | Служба Intune обнаружила, что пользователь работает с устройством, где снято ограничение на доступ к файловой системе. | Выполните сброс устройства до заводских параметров по умолчанию. Выполните [эти инструкции](https://support.apple.com/HT201274) на сайте службы поддержки Apple.
**Требуется подключение к Интернету**: чтобы подтвердить, что вы можете использовать это приложение, требуется подключение к Интернету. | Это устройство не подключено к Интернету. | Подключите устройство к сети Wi-Fi или сети данных.
**Неизвестная ошибка**: попробуйте перезапустить приложение. Если проблема повторится, обратитесь за помощью к ИТ-администратору. | Произошла неизвестная ошибка. | Подождите некоторое время и повторите попытку. Если ошибка повторяется, создайте [запрос в службу поддержки](../fundamentals/get-support.md#create-an-online-support-ticket) для Intune.
**Осуществляется доступ к данным организации**: у указанной вами рабочей или учебной учетной записи нет доступа к этому приложению. Возможно, вам потребуется войти в систему с помощью другой учетной записи. Для получения дополнительных сведений обратитесь к ИТ-администратору. | Служба Intune обнаружила попытку пользователя выполнить вход с использованием второй рабочей или учебной учетной записи, которая отличается от учетной записи, зарегистрированной в системе MAM для данного устройства. Одновременно система MAM может управлять только одной рабочей или учебной учетной записью для каждого устройства. | Попросите пользователя войти с использованием учетной записи, имя которой изначально указано на экране входа. Может потребоваться [настроить параметр UPN пользователя для Intune](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm). <br> <br> Если же пользователь входит в систему с помощью новой рабочей или учебной учетной записи, удалите ранее зарегистрированную учетную запись MAM.
**Проблема с подключением**: возникла непредвиденная проблема с подключением. Проверьте подключение и повторите попытку.  |  Непредвиденный сбой. | Подождите некоторое время и повторите попытку. Если ошибка повторяется, создайте [запрос в службу поддержки](../fundamentals/get-support.md#create-an-online-support-ticket) для Intune.
**Оповещение**: это приложение больше нельзя использовать. Для получения дополнительных сведений обратитесь к ИТ-администратору. | Не удалось проверить сертификат приложения. | Убедитесь, что установлена актуальная версия приложения. <br><br> Переустановите приложение.
**Ошибка**: в этом приложении возникла проблема, поэтому его нужно закрыть. Если ошибка повторится, обратитесь к ИТ-администратору. | Сбой при чтении ПИН-кода приложения MAM из цепочки ключей Apple iOS. | Перезагрузите устройство. Убедитесь, что установлена актуальная версия приложения. <br><br> Переустановите приложение.

### <a name="error-messages-and-dialogs-on-android"></a>Сообщения об ошибках и диалоговые окна с ошибками в Android

Диалоговое окно или сообщение об ошибке | Причина | Серверы |
-- | --- | --- |
**Приложение не настроено**: это приложение не настроено для использования. Для получения дополнительных сведений обратитесь к ИТ-администратору. | Не удалось обнаружить требуемую политику защиты для приложения. |Убедитесь, что политика защиты приложений Android развернута для группы безопасности пользователя и нацелена на это приложение.
**Сбой при запуске приложения**: возникла проблема при запуске приложения. Попробуйте обновить данное приложение или приложение корпоративного портала. Если вам нужна помощь, обратитесь к системному администратору. | Служба Intune обнаружила допустимую политику защиты приложений для приложения, однако во время инициализации MAM происходит аварийное завершение работы приложения. | Убедитесь, что установлена актуальная версия приложения. <br><br> Убедитесь, что на устройстве установлена актуальная версия приложение корпоративного портала. <br><br> Если ошибка повторяется, воспользуйтесь приложением "Корпоративный портал" для отправки журналов Intune или создайте [запрос в службу поддержки](../fundamentals/get-support.md#create-an-online-support-ticket).
**Приложения не найдены**: на этом устройстве нет приложений, в которых ваша организация разрешает открывать это содержимое. Для получения дополнительных сведений обратитесь к ИТ-администратору. | Пользователь попытался открыть рабочие или учебные данные с помощью другого приложения, но Intune не удается найти другие управляемые приложения, которым разрешено открывать эти данные. | Убедитесь, что политика защиты приложений Android развернута для группы безопасности пользователя и нацелена по меньшей мере на одно другое приложение с поддержкой MAM, которое может открывать указанные данные.
**Не удалось войти в систему**: попробуйте войти еще раз. Если проблема повторится, обратитесь за помощью к ИТ-администратору. | Не удалось проверить подлинность учетной записи, с помощью которой пользователь попытался выполнить вход. | Убедитесь, что пользователь выполняет вход с помощью рабочей или учебной учетной записи, которая уже зарегистрирована в службе MAM Intune (первая рабочая или учебная учетная запись, с помощью которой успешно выполнен вход в это приложение). <br><br> Очистите данные приложения. <br><br> Убедитесь, что установлена актуальная версия приложения. <br><br> Убедитесь, что установлена последняя версия корпоративного портала.
**Требуется подключение к Интернету**: чтобы подтвердить, что вы можете использовать это приложение, требуется подключение к Интернету. | Это устройство не подключено к Интернету. | Подключите устройство к сети Wi-Fi или сети данных.
**Устройство не соответствует требованиям**: это приложение невозможно использовать, так как это устройство рутировано. Для получения дополнительных сведений обратитесь к ИТ-администратору. | Служба Intune обнаружила, что пользователь работает с рутированным устройством. | Выполните сброс устройства до заводских параметров по умолчанию.
**Учетная запись не настроена**: управление этим приложением должно вестись в Microsoft Intune, но у вас не настроена учетная запись. Для получения дополнительных сведений обратитесь к ИТ-администратору. | У учетной записи пользователя нет лицензии Intune A Direct. | Убедитесь, что на [портале администрирования Microsoft 365](https://admin.microsoft.com) учетной записи пользователя назначена лицензия Intune.
**Не удается зарегистрировать приложение**: управление этим приложением должно вестись в Microsoft Intune, но зарегистрировать его сейчас не удалось. Для получения дополнительных сведений обратитесь к ИТ-администратору. | Не удается автоматически зарегистрировать приложение в службе MAM, когда требуется политика защиты приложений. | Очистите данные приложения. <br><br> Отправьте журналы в Intune через приложение "Корпоративный портал" или отправьте запрос в службу поддержки. Дополнительные сведения см. в разделе [Как получить поддержку для Microsoft Intune](../fundamentals/get-support.md).

## <a name="next-steps"></a>Дальнейшие шаги

- [Проверка настройки управления мобильными приложениями](app-protection-policies-validate.md)
- Сведения об использовании файлов журнала для устранения неполадок Защита приложений Intune политике см. в разделе [https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-Intune-app-protection-policy-using/ba-p/330372](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-Intune-app-protection-policy-using/ba-p/330372)
- Дополнительные сведения об устранении неполадок в службе Intune см. в руководстве по [использованию портала диагностики для оказания помощи пользователям в вашей компании](../fundamentals/help-desk-operators.md). 
- Вы можете узнать об известных проблемах в Microsoft Intune. См. статью [Известные проблемы в Microsoft Intune](../known-issues.md).
- Нужна дополнительная помощь? См. [ Получение поддержки для Microsoft Intune](../fundamentals/get-support.md).