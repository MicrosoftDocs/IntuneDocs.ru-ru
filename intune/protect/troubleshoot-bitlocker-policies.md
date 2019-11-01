---
title: Советы по устранению неполадок для политик BitLocker в Microsoft Intune
titleSuffix: Microsoft Intune
description: Описание включения шифрования BitLocker на устройстве с помощью политики Intune и проверки успешного развертывания политики на устройстве.
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 440eb2d457783ac71b905d064a6d83abaa966cfe
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503906"
---
# <a name="troubleshoot-bitlocker-policies-in-microsoft-intune"></a>Устранение неполадок в политиках BitLocker в Microsoft Intune

Эта статья поможет администраторам Intune понять, как устройства Windows 10 настраивают BitLocker на основе политики Intune. В этой статье также приводятся рекомендации по устранению проблем с параметрами BitLocker на устройствах, управляемых с помощью Intune.  

## <a name="understanding-bitlocker"></a>Основные сведения о BitLocker

Шифрование диска BitLocker — это служба, предлагаемая операционными системами Microsoft Windows, которая позволяет пользователям шифровать данные на жестких дисках. BitLocker поддерживает шифрование дисков операционной системы, съемных носителей и фиксированных дисков данных. BitLocker также поддерживает использование 256-разрядного шифрования для лучшей защиты конфиденциальных данных.  

С помощью Microsoft Intune вы можете управлять BitLocker на устройствах Windows 10 с помощью следующих методов:

- **Политики конфигурации устройств** . Некоторые встроенные параметры политики доступны в консоли администрирования Intune в **конфигурации устройства**  > **Endpoint Protection**  > **политики шифрования Windows**. Все доступные коммутаторы и функции можно найти здесь: [Шифрование Windows](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption).

- **Базовые показатели безопасности**  - [базовых показателей безопасности](security-baselines.md) — это известные группы параметров и значения по умолчанию, рекомендованные соответствующей группой безопасности для защиты устройств Windows. Различные базовые источники, такие как *базовый план безопасности MDM* или *базовый уровень ATP в защитнике Майкрософт* , могут управлять теми же параметрами, что и другие параметры. Они также могут управлять теми же параметрами, которые управляются с помощью политик конфигурации устройств. 

Помимо Intune, параметры BitLocker могут управляться другими способами, такими как групповая политика или вручную заданы пользователем устройства.

Независимо от того, как параметры применяются к устройству, политики BitLocker используют [BitLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) для настройки шифрования на устройстве. Средство шифрования BitLocker встроено в Windows, и, когда Intune развертывает политику BitLocker на назначенном устройстве, это средство шифрования BitLocker на устройстве, которое записывает соответствующие значения в реестр Windows, чтобы параметры политики вступили в силу.

Если вы хотите узнать больше о BitLocker, см. следующие ресурсы.

- [BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [Общие сведения о решении BitLocker и вопросы и требования](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview-and-requirements-faq)

Теперь, когда у вас есть общее представление о том, что делают эти политики и как они работают, посмотрите, как можно проверить, успешно ли параметры BitLocker применены к клиенту Windows.

## <a name="verify-the-source-of-bitlocker-settings"></a>Проверка источника параметров BitLocker

При исследовании проблемы BitLocker на устройстве с Windows 10 важно сначала определить, связана ли эта ошибка с Intune или Windows. После того как вероятный источник сбоя будет известен, вы сможете сосредоточиться на действиях по устранению неполадок в нужном месте и, если необходимо, получить поддержку от правильной команды.  

В качестве первого шага определите, успешно ли развернута политика Intune на целевом устройстве. В следующем примере имеется политика конфигурации устройства, которая развертывает параметры шифрования Windows (BitLocker), как показано ниже. 

![Политика конфигурации устройств шифрования Windows с параметрами](./media/troubleshooting-bitlocker-policies/settings.png)

Как проверить, применены ли параметры к целевому устройству? Ниже приведены несколько способов.

### <a name="device-configuration-policy-device-status"></a>Состояние устройства политики конфигурации устройств  

При использовании политики конфигурации устройств для настройки BitLocker можно проверить состояние политики на портале Intune. На портале последовательно выберите **Конфигурация устройства**  > **Профили** > выберите профиль, содержащий параметры BitLocker, а затем щелкните **состояние устройства**. В списке отображаются устройства, назначенные профилю, а в столбце *состояние устройства* указывается, успешно ли развернуто устройство в профиле. 

Помните, что между устройством, получающим политику BitLocker, может быть задержка, а диск полностью зашифрован.  

 
### <a name="use-control-panel-on-the-client"></a>Использование панели управления на клиенте  

На устройстве с включенным BitLocker и шифровании диска можно просмотреть состояние BitLocker с помощью панели управления "устройства". На устройстве откройте **Панель управления**  > **система и безопасность**  > **Шифрование диска BitLocker**. Подтверждение отображается, как показано на следующем рисунке.  

![BitLocker включен на панели управления](./media/troubleshooting-bitlocker-policies/control-panel.png)

### <a name="use-a-command-prompt"></a>С использованием командной строки  

На устройстве с включенным шифрованием BitLocker и шифровании диска запустите командную строку с учетными данными администратора, а затем запустите `manage-bde -status`. Результат должен быть примерно таким:  
![A результата команды Status ](./media/troubleshooting-bitlocker-policies/command.png)

В данном примере: 
- **Защита BitLocker** включена **,**  
- **Зашифровано в процентах** — **100%**  
- **Метод шифрования** — **XTS-AES 256**.  

Вы также можете проверить **предохранители ключа** , выполнив следующую команду:

```cmd
Manage-bde -protectors -get c:
```

Или с помощью PowerShell:

```powershell
Confirm-SecureBootUEFI
```

### <a name="review-the-devices-registry-key-configuration"></a>Проверьте конфигурацию раздела реестра Devices.   

После успешного развертывания политики BitLocker на устройстве просмотрите следующий раздел реестра на устройстве, где можно просмотреть конфигурацию параметров BitLocker: *HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\current\device\BitLocker* . Пример:

![Раздел реестра BitLocker](./media/troubleshooting-bitlocker-policies/registry.png)

Эти значения настраиваются с помощью средства шифрования BitLocker. Убедитесь, что значения ключей соответствуют параметрам, указанным в источнике политики шифрования Windows Intune. Дополнительные сведения о каждом из этих параметров см. в разделе [BitLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp).

> [!NOTE]
> Просмотр событий Windows также будет содержать различные сведения, связанные с BitLocker. Здесь слишком много для перечисления, но поиск в **API BitLocker** предоставит вам много полезных сведений.

### <a name="check-the-mdm-diagnostics-report"></a>Проверка отчета о диагностике MDM  

На устройстве с включенным BitLocker можно создать и просмотреть диагностический отчет MDM с целевого устройства, чтобы убедиться в наличии политики BitLocker. Если вы видите параметры политики в отчете, это еще одно уведомление о том, что политика успешно развернута. Видеоролик *Майкрософт* по этой ссылке содержит сведения о том, как записать диагностический отчет MDM с устройства Windows. 

> [!VIDEO https://www.youtube.com/embed/WKxlcjV4TNE]

При анализе отчета о диагностике MDM содержимое может показаться немного запутанным. Ниже приведен пример, в котором показано, как сопоставить содержимое отчета с параметрами политики.

![Пример отчета о диагностике MDM](./media/troubleshooting-bitlocker-policies/report.png)

В результате выходных данных отобразятся значения, соответствующие значениям из политики BitLocker:

![Результат вывода показывает значения ](./media/troubleshooting-bitlocker-policies/output.png)

Результаты диагностики MDM:

```asciidoc
EncryptionMethodWithXtsOsDropDown: 7 (The value 7 refers to the 256 bit encryption)
EncryptionMethodWithXtsFdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
EncryptionMethodWithXtsRdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
```

Чтобы узнать, что означает каждое значение, можно обратиться к [документации по CSP для BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) . В этом примере фрагмент является общим на следующем рисунке.

![Назначение значений](./media/troubleshooting-bitlocker-policies/shared-example.png)

 Аналогичным образом можно просмотреть все значения и проверить их с помощью ссылки BitLocker CSP.

> [!TIP]
> Основной целью диагностического отчета MDM является помощь служба поддержки Майкрософт при устранении неполадок. Если вы откроете обращение в службу поддержки для Intune, а проблема касается клиентов Windows, всегда рекомендуется собрать этот отчет и включить его в запрос в службу поддержки.

## <a name="troubleshooting-bitlocker-policy"></a>Устранение неполадок политики BitLocker

Теперь у вас есть хорошее представление о том, как убедиться, что политика BitLocker успешно развернута с помощью Intune, которая передает конфигурацию BitLocker в CSP BitLocker в WIndows.  

**Политика не может подключиться к устройству,** если ваша политика Intune отсутствует в емкости:  
- **Устройство правильно зарегистрировано в Microsoft Intune?** В противном случае необходимо решить эту проблемы, прежде чем устранять неполадки, связанные с политикой. Справку по устранению неполадок, связанных с регистрацией Windows, можно найти [здесь](../enrollment/troubleshoot-windows-enrollment-errors.md).  
- **Есть ли на устройстве активное сетевое подключение?** Если устройство находится в режиме "в самолете" или отключено, или если устройство находится в расположении без службы, то политика не будет доставлена или применена до восстановления сетевого подключения.  
- **Была ли политика BitLocker развернута для нужной группы пользователей или устройств?** Убедитесь, что пользователь или устройство является членом целевых групп.  

**Политика установлена, но не все параметры настроены** . Если политика Intune достигает устройства, но не все конфигурации установлены:  
- **Завершится ли развертывание всей политики или только некоторые параметры, которые не применяются?** Если вы столкнулись с ситуацией, когда не применяются только некоторые параметры политики, ознакомьтесь со следующими замечаниями.

  1. **Не все параметры BitLocker поддерживаются во всех версиях Windows**.  
  Политика переключается на устройство как единое целое, поэтому, если некоторые параметры применяются, а другие — нет, вы можете быть уверены, что сама политика получена. В этом сценарии версия Windows на устройстве может не поддерживать проблемные параметры. Дополнительные сведения о требованиях к версии для каждого параметра см. в разделе [BitLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) в документации Windows.  

  1. **BitLocker не поддерживается на всех устройствах**.  
  Даже если у вас установлена правильная версия Windows, возможно, оборудование базового устройства не соответствует требованиям к шифрованию BitLocker. [Системные требования для BitLocker (https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements) в документации по Windows, но основное средство проверки заключается в том, что устройство имеет совместимую микросхему доверенного платформенного модуля (1,2 или более поздней версии) и совместимую с организация TCG (TCG) микропрограмму BIOS или UEFI.

**Пример расследования** . вы развертываете политику BitLocker на устройстве с Windows 10, а параметр " **шифровать устройства** " отображает состояние **ошибки** на портале.

- Как видно из названия, этот параметр позволяет администратору требовать включения шифрования с помощью *BitLocker > шифрования устройства*. С помощью советов по устранению неполадок, упомянутых ранее, вы сначала проверяете отчет о диагностике MDM. Отчет подтверждает, что на устройстве была развернута правильная политика:

  ![Отчет подтверждает, что на устройстве развернута правильная политика](./media/troubleshooting-bitlocker-policies/mdm-report.png)

- Вы также можете проверить успешность в реестре:

  ![Значение реестра Рекуиреддевицеенкриптион показывает 1](./media/troubleshooting-bitlocker-policies/registry-confirm.png)

- Затем вы проверяете состояние TPM с помощью PowerShell и обнаружите, что TPM недоступен на устройстве:

  ![Состояние проверенного TPM с помощью PowerShell](./media/troubleshooting-bitlocker-policies/tpm-command.png)

- Поскольку BitLocker полагается на доверенный платформенный модуль, вы можете заключить, что BitLocker не завершится сбоем из-за проблемы с Intune или политикой, а потому, что само устройство не имеет микросхемы TPM или модуль TPM отключен в BIOS.

  В качестве дополнительного Совета вы можете подтвердить то же самое в Просмотр событий Windows в разделе **журналы приложений и служб**  > **Windows**  > **BitLocker API**. В журнале событий **BitLocker API** вы найдете событие с идентификатором 853, которое означает, что TPM недоступен:

  ![Событие с идентификатором 853](./media/troubleshooting-bitlocker-policies/event-error.png)

  > [!NOTE]
  > Состояние доверенного платформенного модуля можно также проверить, запустив **TPM. msc** на устройстве.



## <a name="summary"></a>Сводка

При устранении неполадок политики BitLocker в Intune и подтверждении того, что политика достигает предполагаемого устройства, можно считать, что проблема не связана напрямую с Intune. Скорее всего, проблема связана с операционной системой Windows или оборудованием. В этом случае начните искать в других областях, таких как конфигурация TPM или UEFI и безопасная загрузка).

<!-- Unable to Verify this: 
You can try to isolate the issue by enabling BitLocker manually. If you can turn on BitLocker manually, Intune won't be able to turn it on through policy. Also, the Windows Recovery Environment (WinRE) must be enabled on the client for BitLocker to work. When organizations use using custom images, WinRE is a common cause that is often overlooked. 
-->

## <a name="next-steps"></a>Дальнейшие шаги  

Ниже приведены дополнительные ресурсы, которые могут помочь при работе с BitLocker.

- [Документация по продукту BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [Требования к системе для BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements)
- [Часто задаваемые вопросы о BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-frequently-asked-questions)
- [Документация по CSP для BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)
- [Параметры политики шифрования Windows Intune](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption)
- [Аппаратно-независимое шифрование BitLocker с помощью AAD/MDM](https://blogs.technet.microsoft.com/home_is_where_i_lay_my_head/2017/06/07/hardware-independent-automatic-bitlocker-encryption-using-aadmdm/)
- [Политика CSP для шифрования BitLocker на устройствах с автоматической пилотной программой](https://techcommunity.microsoft.com/t5/Windows-10-security/CSP-policy-for-bitLocker-encryption-on-autopilot-devices/m-p/284537)
- [Пошаговое руководство по созданию и развертыванию политики BitLocker с помощью Intune](https://blogs.technet.microsoft.com/cbernier/2017/07/11/windows-10-intune-windows-bitlocker-management-yes/)