---
title: "Устройства | Документация Майкрософт"
description: "Справочник по категории \"Устройства\" коллекций сущностей в API хранилища данных Intune."
keywords: "Хранилище данных Intune"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6955E12D-70D7-4802-AE3B-8B276F01FA4F
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 8013d7f091c154709f0dd98dcda2e7f5f09056d2
ms.sourcegitcommit: addf6a40caa22c22adfd2e2eff7d666cd1877e3c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2017
---
# <a name="reference-for-devices-entities"></a>Справочник по сущностям устройств

Категория **Устройства** содержит сущности для мобильных устройств, отслеживающие указанную ниже информацию:

  -  Тип устройства
  -  Состояние регистрации устройства
  -  Владение устройствами
  -  Состояние управления устройства
  -  Состояние членства устройства в Azure AD
  -  Состояние регистрации
  -  Исторические сведения об устройстве
  -  Инвентаризация приложений на устройстве

## <a name="devicetypes"></a>DeviceTypes

Сущность **DeviceTypes** представляет тип устройства, на который ссылаются другие сущности хранилища данных. Тип устройства обычно описывает модель устройства, изготовителя или их сочетание.

| Свойство  | Описание |
|---------|------------|
| DeviceTypeID |Уникальный идентификатор для типа устройства |
| DeviceTypeKey |Уникальный идентификатор для типа устройства в хранилище данных — суррогатный ключ |
| DeviceTypeName |Тип устройства |

## <a name="example"></a>Пример

| deviceTypeID  | Имя | Описание |
|---------|------------|--------|
| 0 |Настольные |Устройство Windows Desktop |
| 1 |WindowsRT |Устройство Windows RT |
| 2 |WinMO6 |Устройство Windows Mobile 6.0 |
| 3 |Nokia |Устройство Nokia |
| 4 |WindowsPhone |Устройство Windows Phone |
| 5 |Mac |Устройство Mac |
| 6 |WinCE |Устройство Windows CE |
| 7 |WinEmbedded |Устройство Windows Embedded |
| 8 |IPhone |Устройство iPhone |
| 9 |IPad |Устройство iPad |
| 10 |IPod |Устройство iPod |
| 11 |Android |Устройство Android, управляемое с помощью администратора устройств |
| 12 |ISocConsumer |Бытовое устройство iSoc |
| 14 |MacMDM |Устройство Mac OS X, управляемое с помощью встроенного агента MDM |
| 15 |HoloLens |Устройство HoloLens |
| 16 |SurfaceHub |Устройство Surface Hub |
| 17 |AndroidForWork |Устройство Android, управляемое с помощью Android for Work Profile Owner |
| 100 |Blackberry |Устройство Blackberry |
| 101 |Palm |Устройство Palm |
| 255 |Неизвестно |Неизвестный тип устройства |

## <a name="clientregistrationstatetypes"></a>ClientRegistrationStateTypes

Сущность **ClientRegistrationStateTypes** представляет тип устройства, на который ссылаются другие таблицы хранилища данных.

| Свойство  | Описание |
|---------|------------|
| clientRegisterationStateID |Уникальный идентификатор для состояния регистрации |
| clientRegisterationStateKey |Уникальный идентификатор для состояния регистрации в хранилище данных — суррогатный ключ |
| clientRegisterationStateName |Состояние регистрации |

## <a name="example"></a>Пример

| ClientRegisterationStateID  | Имя | Описание |
|---------|------------|--------|
| 0 |NotRegistered |Не зарегистрировано |
| 1 |SMSIDConflict |Конфликт идентификаторов SMS |
| 2 |Зарегистрировано |Зарегистрировано |
| 3 |Revoked |Это состояние означает, что ИТ-администратор заблокировал клиент, и клиент может быть разблокирован. Устройство также может находиться в состоянии "Revoked" после очистки или снятия с учета. |
| 4 |KeyConflict |Конфликт ключей |
| 5 |ApprovalPending |Ожидает утверждения |
| 6 |ResetCert |Сброс сертификата |
| 7 |NotRegisteredPendingEnrollment |Не зарегистрировано, ожидает регистрации |
| 8 |Неизвестно |Неизвестное состояние |

## <a name="enrollmenttypes"></a>EnrollmentTypes

Сущность **EnrollmentTypes** показывает, как было зарегистрировано устройство. Тип регистрации указывает метод регистрации. В примерах указан список различных типов регистрации и их значений.

| Свойство  | Описание |
|---------|------------|
| managementStateID |Уникальный идентификатор для состояния управления. |
| managementStateKey |Уникальный идентификатор для состояния управления в хранилище данных — суррогатный ключ. |
| managementStateName |Указывает состояние удаленного действия, примененного к этому устройству. |

## <a name="example"></a>Пример

| enrollmentTypeID  | Имя | Описание |
|---------|------------|--------|
| 0 |Неизвестно |Неизвестный тип регистрации |
| 1 |UserEnrollment |Регистрация, инициированная пользователем |
| 2 |DeviceEnrollment |Регистрация устройства с профилем без пользователей |
| 3 |DeviceEnrollmentWithUDA |Регистрация устройства с профилем UDA |
| 4 |AzureDomainJoined |Инициированная пользователем регистрация устройства с использованием Azure Active Directory |
| 5 |UserEnrollmentWithServiceAccount |Инициированная пользователем регистрация с использованием учетной записи службы |
| 6 |DepDeviceEnrollment |Регистрация устройства DEP с профилем без пользователей |
| 7 |DepDeviceEnrollmentWithUDA |Регистрация устройства DEP с профилем UDA |
| 8 |AutoEnrollment |Совместная регистрация DRS и MDM для сценария BYOD |

## <a name="ownertypes"></a>OwnerTypes

Сущность **EnrollmentTypes** указывает, является ли устройство корпоративным, личным, или его принадлежность неизвестна.

| Свойство  | Описание | Пример |
|---------|------------|--------|
| ownerTypeID |Уникальный идентификатор для типа владельца | |
| ownerTypeKey |Уникальный идентификатор для типа владельца в хранилище данных — суррогатный ключ | |
| ownerTypeName |Представляет тип владельца устройств: Company — устройство принадлежит предприятию. Personal — устройство является личным (BYOD).  Unknown — информация об этом устройстве отсутствует. |Company Personal Unknown |

## <a name="mdmstatuses"></a>MdmStatuses

Сущность **MdmStatuses** показывает состояние соответствия устройства.

| Свойство  | Описание | Пример |
|---------|------------|--------|
| MdmStatusName |Идентификатор MdmStatus |0 — неизвестно, 1 — соответствует, 2 — не соответствует |
| MdmStatusKey |Уникальный идентификатор для состояния соответствия в хранилище данных — суррогатный ключ | |

## <a name="managementstates"></a>ManagementStates

Сущность **ManagementStates** содержит подробные сведения о состоянии устройства. Они могут оказаться полезными в случаях, когда применяются удаленные действия, на устройстве получен корневой доступ или выполнен взлом ОС.

| Свойство  | Описание |
|---------|------------|
| managementStateID |Уникальный идентификатор для состояния управления |
| managementStateKey |Уникальный идентификатор для состояния управления в хранилище данных — суррогатный ключ |
| managementStateName |Указывает состояние удаленного действия, примененного к этому устройству. |

## <a name="example"></a>Пример

| managementStateID  | Имя | Описание |
|---------|------------|--------|
| 0 |Управляемые |Управляется без ожидающих удаленных действий. |
| 1 |RetirePending |Для устройства имеется ожидающая команда по снятию с учета. |
| 2 |RetireFailed |На устройстве произошел сбой команды по снятию с учета. |
| 3 |WipePending |Для устройства имеется ожидающая команда очистки. |
| 4 |WipeFailed |На устройстве произошел сбой команды очистки. |
| 5 |Unhealthy |Неработоспособное состояние |
| 6 |DeletePending |Для устройства имеется ожидающая команда удаления. |
| 7 |RetireIssued |Для устройства выдана команда по снятию с учета. |
| 8 |WipeIssued |Выдана команда очистки. |
| 9 |WipeCanceled |Команда очистки отменена. |
| 10 |RetireCanceled |Команда по снятию с учета отменена. |
| 11 |Discovered |Устройство было недавно обнаружено Intune, при первой отметке оно будет переведено в состояние управляемого. |

## <a name="workplacejoinstatetypes"></a>WorkPlaceJoinStateTypes

Сущность **WorkPlaceJoinStateTypes** представляет состояние подключения к рабочему месту Azure Active Directory для устройства.  Рабочий процесс регистрации может использовать один или несколько сертификатов для проверки подлинности и иных проверок. При регистрации рабочего места устройства эти сертификаты используются для проверки устройства и пользователя. Выдача сертификатов осуществляется через сервер SCEP. Значения в сущности указывают на различные состояния, в которых устройство может находиться в рамках данного процесса. Некоторые из этих состояний подразумевают ошибку подключения к рабочему месту из-за сбоя при выдаче нужного сертификата (с сервера SCEP). Если устройство никогда не проходило эту процедуру, устанавливается значение "Unknown".

| Свойство  | Описание |
|---------|------------|
| WorkPlaceJoinStateID |Уникальный идентификатор для состояния подключения к рабочему месту |
| WorkPlaceJoinStateKey |Уникальный идентификатор для состояния подключения к рабочему месту в хранилище данных — суррогатный ключ |
| WorkPlaceJoinStateName |Состояние подключения к рабочему месту |

## <a name="example"></a>Пример

| workPlaceJoinStateID  | Имя | Описание |
|---------|------------|--------|
| 0 |Неизвестно |Если устройство не подключено к рабочему месту, оно находится в состоянии "Unknown" |
| 1 |успешно |Успешно подключено к рабочему месту |
| 2 |FailureToGetScepMetadata |Не удалось получить метаданные SCEP |
| 3 |FailureToGetScepChallenge |Не удалось получить запрос защиты SCEP |
| 4 |DeviceFailureToInstallScepCommand |Не удалось установить команду SCEP на устройстве |
| 5 |DeviceFailureToGetCertificate |Устройству не удалось получить сертификат через SCEP |
| 6 |DeviceScepPending |Состояния ожидания; устройство все еще проходит процедуру SCEP |
| 7 |DeviceScepFailed |Устройству не удалось установить сертификат через SCEP |
| 8 |AADValidationFailed |Не удалось проверить существование устройства в AAD |

## <a name="managementagenttypes"></a>ManagementAgentTypes

Сущность **ManagementAgentTypes** представляет агентов, используемых для управления устройством.

| Свойство  | Описание |
|---------|------------|
| ManagementAgentTypeID |Уникальный идентификатор для типа агента управления |
| ManagementAgentTypeKey |Уникальный идентификатор для типа агента управления в хранилище данных — суррогатный ключ |
| ManagementAgentTypeName |Указывает, какой тип агента используется для управления устройством. |

## <a name="example"></a>Пример

| ManagementAgentTypeID  | Имя | Описание |
|---------|------------|--------|
| 1 |EAS |Устройство управляется с помощью Exchange Active Sync |
| 2 |MDM |Устройство управляется с помощью агента MDM |
| 3 |EasMdm |Устройство управляется с помощью Exchange Active Sync и агента MDM |
| 4 |IntuneClient |Устройство управляется агентом Intune для компьютера |
| 5 |EasIntuneClient |Устройство управляется с помощью Exchange Active Sync и агента Intune для компьютера |
| 8 |ConfigManagerClient |Устройство управляется агентом System Center Configuration Manager |
| 16 |Неизвестно |Неизвестный тип агента управления |

## <a name="devices"></a>Устройства

Сущность **Devices** перечисляет все управляемые зарегистрированные устройства и их соответствующие свойства.

| Свойство  | Описание |
|---------|------------|
| DeviceKey |Уникальный идентификатор для устройства в хранилище данных — суррогатный ключ |
| DeviceId |Уникальный идентификатор устройства |
| DeviceName |Имя устройства на платформах, допускающих именование устройства. На других платформах Intune создает имя из других свойств. Этот атрибут может быть доступен не для всех устройств. |
| DeviceTypeKey |Ключ атрибута типа устройства для этого устройства |
| ClientRegisterationStateKey |Ключ атрибута состояния регистрации клиента для этого устройства |
| OwnerTypeKey |Ключа атрибута типа владельца для этого устройства: corporate, personal или unknown. |
| objectSourceKey |Игнорируйте этот столбец. |
| CreatedDate |Дата регистрации устройства |
| LastContact |Последняя известная отметка устройства в Intune |
| LastContactNotification |Последнее уведомление об отметке в Intune, выданное Intune устройству |
| LastContactWorkplaceJoin |Метка времени, указывающая последнее известное состояние подключения к рабочему месту для этого устройства. |
| ManagementAgentKey |Ключ агента управления, сопоставленный с этим устройством. |
| ManagementStateKey |Ключ состояния управления, сопоставленный с этим устройством, который указывает последнее состояние удаленного действия либо наличие корневого доступа или взлома ОС. |
| ReferenceId |Идентификатор устройства в Azure Active Directory |
| WorkPlaceJoinStateKey |Ключ состояния подключения к рабочему месту, сопоставленный с этим устройством. |
| CategoryId |Игнорируйте этот столбец. |
| EnrollmentTypeKey |Ключ типа регистрации, сопоставленный с этим устройством, который указывает метод регистрации. |
| CertExpirationDate |Дата окончания срока действия для сертификата управления MDM. |
| MdmStatusKey |Ключ для MdmStatus |
| OSFamily |Семейство ОС (Windows, iOS, Android и т. п.) |
| OSVersion |Версия ОС |
| OSMajorVersion |Компонент основного номера версии в версии ОС (основной.дополнительный.сборка.редакция) |
| OSMinorVersion |Компонент дополнительного номера версии в версии ОС (основной.дополнительный.сборка.редакция) |
| OSBuildNumber |Компонент версии сборки в версии ОС (основной.дополнительный.сборка.редакция) |
| OSRevisionNumber |Компонент версии редакции в версии ОС (основной.дополнительный.сборка.редакция) |
| EasID |Идентификатор EAS этого устройства, если оно управляется Exchange Active Sync. |
| GraphDeviceIsManaged |Последнее состояние управления, заданное Intune в AAD |
| GraphDeviceIsCompliant |Последнее состояние соответствия, заданное Intune в AAD |
| SerialNumber |Серийный номер устройства при его наличии |
| EnrolledByUser |Идентификатор пользователя, зарегистрировавшего это устройство, который ссылается на столбец userId в таблице пользователя. |
| RowLastModifiedDateTimeUTC |Время последнего изменения этой записи. |
| ProcessorArchitecture |Архитектура процессора |
| DeviceAction |Последнее выполненное действие устройства, пока игнорируйте. |
| Изготовитель |Производитель устройства |
| Модель |Модель устройства |
| LastPolicyUpdateUtc |Время последнего изменения политики на устройстве |
| LastExchangeStatusUtc |Время последней синхронизации устройства с Exchange. |
| IsDeleted |Установите значение True, если устройство больше не находится под управлением Intune. Сохраняет последнее известное состояние. |

## <a name="devicepropertyhistory"></a>DevicePropertyHistory

Сущность **DevicePropertyHistory** имеет те же свойства, что и таблица устройств и ежедневные моментальные снимки каждой записи устройств за последние 90 дней. Столбец DateKey указывает день для каждой строки.

| Свойство  | Описание |
|---------|------------|
| DateKey |Ссылка на таблицу дат с указанием дня |
| DeviceKey |Уникальный идентификатор для устройства в хранилище данных — суррогатный ключ. Это ссылка на таблицу устройства, содержащую идентификатор устройства Intune. |
| DeviceModel |Модель устройства |
| ОС |Операционная система устройства |
| DeviceName |Имя устройства на платформах, допускающих именование устройства. На других платформах Intune создает имя из других свойств. Этот атрибут может быть доступен не для всех устройств. |
| SoftwareVersion |В большинстве случаев это версия ОС, только на платформах Apple это значение отличается от версии ОС. |
| Imei |Номер IMEI |
| HardwareInventoryTimeUtc |Время первой инвентаризации для этого устройства. |
| InventoryModifiedTimeUtc |Время сохранения последней инвентаризации при создании этого моментального снимка |
| InventoryReportingTimeUtc |Время сбора последней инвентаризации для этого устройства |
| ExchangeActiveSyncId |Идентификатор устройства Exchange ActiveSync |
| ComputerSystemDescription |Описание системы |
| ComputerSystemName |Имя системы |
| ComputerSystemManufacturer |Производитель системы |
| ComputerSystemModel |Модель системы |
| UserName |Имя пользователя |
| OSType |Тип ОС |
| OSCaption |Название операционной системы |
| OSName |Имя операционной системы |
| OSManufacturer |Производитель операционной системы |
| OSProductSuite |Набор продуктов операционной системы |
| OSProductType |Тип продуктов операционной системы |
| Локаль |Языковой стандарт операционной системы |
| PhysicalMemoryCapacity |Объем физической памяти (в байтах) |
| PhysicalMemoryRemovable |Объем физической памяти съемного носителя (в байтах) |
| SystemEnclosureChassisTypesInnerText |Определяет тип системного шасси для этого устройства. Числа обозначают следующее: 0 или пусто — неизвестно, 1 — настольная система, 2 — ноутбук, 3 — рабочая станция, 4 — корпоративный сервер, 100 — телефон, 101 — планшет, 102/103 — другой неизвестный тип мобильного устройства |
| SystemEnclosureModel |Модель системного корпуса |
| SystemEnclosureSerialNumber |Серийный номер системного корпуса |
| NetworkAdapterConfigurationText |Текст конфигурации из сетевого адаптера |
| MacAddress |MAC-адрес; |
| SmsID |Идентификатор устройства Intune |
| CertExpiry |Дата окончания срока действия для сертификата управления MDM |
| DeviceClientAgentVersion |Версия агента клиента |
| DeviceClientID |Идентификатор клиента устройства |
| SerialNumber |Серийный номер |
| DeviceManufacturer |Изготовитель устройства |
| DMVersion |Версия DM |
| FirmwareVersion |Версия встроенного ПО |
| HardwareVersion |Версия оборудования |
| PlatformType |Тип платформы |
| ProcessorLevel |Уровень процессора |
| ProcessorRevision |Версия процессора |
| Продукт |Продукт |
| ProductVersion |Версия продукта |
| ПВТ |Поставщик вычислительной техники |
| DeviceBuildVersion |Версия сборки устройства |
| Meid |Идентификатор мобильного оборудования |
| PhoneNumber |Номер телефона |
| SubscriberCarrierNetwork |Имя сети оператора телефонной связи |
| CellularTechnology |Тип сети оператора телефонной связи (CDMA/GSM) |
| Imsi |Номер IMSI |
| JailBroken |Значение True, если на устройстве получен корневой доступ или выполнен взлом ОС. |
| IsActivationLockEnabled |Значение True, если включена Блокировка активации |
| DeviceType |Тип устройства |
| IsSupervised |Защищено |
| DeviceDisplayNumberOfColors |Число цветов у дисплея устройства |
| HorizontalResolution |Горизонтальное разрешение экрана устройства |
| VerticalResolution |Вертикальное разрешение экрана устройства |
| StorageFree |Свободное место для хранения (в байтах) |
| StorageTotal |Общее место для хранения (в байтах) |
| ProgramFree |Свободная память программ (в байтах) |
| ProgramTotal |Общая память программ (в байтах) |
| RemovableStorageFree |Свободная память на съемном носителе (в байтах) |
| RemovableStorageTotal |Общая память на съемном носителе (в байтах) |
| DeviceMemoryDeviceCapacity |Объем памяти устройства |
| DeviceMemoryAvailableDeviceCapacity |Доступный объем памяти устройства |
| DeviceOSVersion |Версия ОС |
| DeviceOSPlatform |Платформа ОС |
| DeviceOSLanguage |Язык ОС |
| PasswordMaxAttemptsBeforeWipe |Максимально допустимое число попыток ввода пароля, прежде чем будет выполнена очистка устройства |
| PasswordMinComplexChars |Минимальное количество сложных символов в пароле |
| PasswordMinLength |Минимальная длина пароля |
| PasswordHistory |Минимальное число непринятых паролей для занесения в журнал |
| PasswordEnabled |Указание того, включен ли пароль |
| PasswordExpiration |Срок действия пароля |
| AllowRecoveryPassword |Разрешить восстановление паролей |
| PasswordAutoLockTimeout |Время ожидания автоматической блокировки |
| PasswordType |Тип пароля |
| BacklightACTimeout |Время ожидания для подсветки при подключении к источнику питания |
| BacklightBatTimeout |Время ожидания для подсветки при работе от батареи |
| PowerBackupPercent |Процент резервирования питания |
| BatteryPercent |Процент оставшегося заряда батареи |
| PlatformID |Идентификатор платформы |
| ExchangeDeviceID |Идентификатор устройства Exchange |
| SmsProcessorDescription |Описание процессора |
| OwnerEmailAddress |Адрес электронной почты владельца |
| DeviceOSName |Имя операционной системы |
| WifiMac |MAC-адрес для Wi-Fi |
| EthernetMac |MAC-адрес для Ethernet |
| RequireEncryption |Указывает, шифруется ли устройство |
| ActivationLockBypassCode |Код обхода Блокировки активации |

## <a name="mdmdeviceinventoryhistories"></a>MdmDeviceInventoryHistories

Сущность **MdmDeviceInventoryHistories** содержит ежедневные моментальные снимки данных инвентаризации для устройств, управляемых с помощью MDM, за последние 90 дней. Столбец DateKey указывает день для строки. Возможно, некоторые свойства невозможно применить или заполнить для всех устройств, поэтому обратитесь к этой странице для получения дополнительных сведений. Дополнительные сведения см. в статье [Получение сведений об устройствах с помощью инвентаризации в Microsoft Intune](https://docs.microsoft.com/Intune-classic/deploy-use/understand-your-devices-with-inventory-in-microsoft-Intune).

| Свойство  | Описание |
|---------|------------|
| DateKey |Ссылка на таблицу дат с указанием дня |
| DeviceKey |Уникальный идентификатор для устройства в хранилище данных — суррогатный ключ. Это ссылка на таблицу устройства, содержащую идентификатор устройства Intune. |
| DeviceModel |Модель устройства |
| ОС |Операционная система устройства |
| DeviceName |Имя устройства на платформах, допускающих именование устройства. На других платформах Intune создает имя из других свойств. Этот атрибут может быть доступен не для всех устройств. |
| SoftwareVersion |В большинстве случаев это версия ОС, только на платформах Apple это значение отличается от версии ОС. |
| Imei |Номер IMEI |
| HardwareInventoryTimeUtc |Время первой инвентаризации для этого устройства. |
| InventoryModifiedTimeUtc |Время сохранения последней инвентаризации при создании этого моментального снимка |
| InventoryReportingTimeUtc |Время сбора последней инвентаризации для этого устройства |
| ExchangeActiveSyncId |Идентификатор устройства Exchange ActiveSync |
| ComputerSystemDescription |Описание системы |
| ComputerSystemName |Имя системы |
| ComputerSystemManufacturer |Производитель системы |
| ComputerSystemModel |Модель системы |
| UserName |Имя пользователя |
| OSType |Тип ОС |
| OSCaption |Название операционной системы |
| OSName |Имя операционной системы |
| OSManufacturer |Производитель операционной системы |
| OSProductSuite |Набор продуктов операционной системы |
| OSProductType |Тип продуктов операционной системы |
| Локаль |Языковой стандарт операционной системы |
| PhysicalMemoryCapacity |Объем физической памяти (в байтах) |
| PhysicalMemoryRemovable |Объем физической памяти съемного носителя (в байтах) |
| SystemEnclosureChassisTypesInnerText |Определяет тип системного шасси для этого устройства. Числа обозначают следующее: 0 или пусто — неизвестно, 1 — настольная система, 2 — ноутбук, 3 — рабочая станция, 4 — корпоративный сервер, 100 — телефон, 101 — планшет, 102/103 — другой неизвестный тип мобильного устройства |
| SystemEnclosureModel |Модель системного корпуса |
| SystemEnclosureSerialNumber |Серийный номер системного корпуса |
| NetworkAdapterConfigurationText |Текст конфигурации из сетевого адаптера |
| MacAddress |MAC-адрес; |
| SmsID |Идентификатор устройства Intune |
| CertExpiry |Дата окончания срока действия для сертификата управления MDM |
| DeviceClientAgentVersion |Версия агента клиента |
| DeviceClientID |Идентификатор клиента устройства |
| SerialNumber |Серийный номер |
| DeviceManufacturer |Изготовитель устройства |
| DMVersion |Версия DM |
| FirmwareVersion |Версия встроенного ПО |
| HardwareVersion |Версия оборудования |
| PlatformType |Тип платформы |
| ProcessorLevel |Уровень процессора |
| ProcessorRevision |Версия процессора |
| Продукт |Продукт |
| ProductVersion |Версия продукта |
| ПВТ |Поставщик вычислительной техники |
| DeviceBuildVersion |Версия сборки устройства |
| Meid |Идентификатор мобильного оборудования |
| PhoneNumber |Номер телефона |
| SubscriberCarrierNetwork |Имя сети оператора телефонной связи |
| CellularTechnology |Тип сети оператора телефонной связи (CDMA/GSM) |
| Imsi |Номер IMSI |
| JailBroken |Значение True, если на устройстве получен корневой доступ или выполнен взлом ОС. |
| IsActivationLockEnabled |Значение True, если включена Блокировка активации |
| DeviceType |Тип устройства |
| IsSupervised |Защищено |
| DeviceDisplayNumberOfColors |Число цветов у дисплея устройства |
| HorizontalResolution |Горизонтальное разрешение экрана устройства |
| VerticalResolution |Вертикальное разрешение экрана устройства |
| StorageFree |Свободное место для хранения (в байтах) |
| StorageTotal |Общее место для хранения (в байтах) |
| ProgramFree |Свободная память программ (в байтах) |
| ProgramTotal |Общая память программ (в байтах) |
| RemovableStorageFree |Свободная память на съемном носителе (в байтах) |
| RemovableStorageTotal |Общая память на съемном носителе (в байтах) |
| DeviceMemoryDeviceCapacity |Объем памяти устройства |
| DeviceMemoryAvailableDeviceCapacity |Доступный объем памяти устройства |
| DeviceOSVersion |Версия ОС |
| DeviceOSPlatform |Платформа ОС |
| DeviceOSLanguage |Язык ОС |
| PasswordMaxAttemptsBeforeWipe |Максимально допустимое число попыток ввода пароля, прежде чем будет выполнена очистка устройства |
| PasswordMinComplexChars |Минимальное количество сложных символов в пароле |
| PasswordMinLength |Минимальная длина пароля |
| PasswordHistory |Минимальное число непринятых паролей для занесения в журнал |
| PasswordEnabled |Указание того, включен ли пароль |
| PasswordExpiration |Срок действия пароля |
| AllowRecoveryPassword |Разрешить восстановление паролей |
| PasswordAutoLockTimeout |Время ожидания автоматической блокировки |
| PasswordType |Тип пароля |
| BacklightACTimeout |Время ожидания для подсветки при подключении к источнику питания |
| BacklightBatTimeout |Время ожидания для подсветки при работе от батареи |
| PowerBackupPercent |Процент резервирования питания |
| BatteryPercent |Процент оставшегося заряда батареи |
| PlatformID |Идентификатор платформы |
| ExchangeDeviceID |Идентификатор устройства Exchange |
| SmsProcessorDescription |Описание процессора |
| OwnerEmailAddress |Адрес электронной почты владельца |
| DeviceOSName |Имя операционной системы |
| WifiMac |MAC-адрес для Wi-Fi |
| EthernetMac |MAC-адрес для Ethernet |
| RequireEncryption |Указывает, шифруется ли устройство |
| ActivationLockBypassCode |Код обхода Блокировки активации |

## <a name="applicationinventory"></a>ApplicationInventory

Сущность **ApplicationInventory** перечисляет приложения, найденные на устройстве во время сбора данных инвентаризации.

| Свойство  | Описание |
|---------|------------|
| DeviceKey |Ссылка на таблицу устройств |
| ApplicationKey |? (копируется из ExchangeDeviceService\DeviceApplication) |
| ApplicationName |? (копируется из ExchangeDeviceService\DeviceApplication) |
| ApplicationVersion |? (копируется из ExchangeDeviceService\DeviceApplication) |
| BundleSize |? (копируется из ExchangeDeviceService\DeviceApplication) |