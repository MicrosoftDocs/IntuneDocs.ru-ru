---
title: Тестирование и проверка Intune
titleSuffix: Microsoft Intune
description: Как в вашей среде выполнять тестирование и проверку в решении Intune, существующем только в облаке.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 3/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4f82ee0c-4bd6-4623-9b10-9249d316ccf5
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: c2ce184a2dbd0ca4b66740f0687302d1ed007878
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505018"
---
# <a name="intune-testing-and-validation"></a>Тестирование и проверка Intune

При тестировании внедрения Microsoft Intune рекомендуется выполнять функциональную проверку и проверку вариантов использования. Функциональная проверка состоит из тестирования каждого компонента, подтверждающего правильность его работы. Проверка вариантов использования подразумевает тестирование с целью убедиться, что сценарии, состоящие из ряда задач, работают должным образом. 

Рекомендуем привлечь к процессу тестирования ИТ-персонал и сотрудников службы поддержки. Это позволит составить сопроводительную документацию и поможет сотрудникам хорошо изучить поддерживаемый продукт. Если компонент или сценарий не работает в установленных вариантах использования, обязательно задокументируйте потребовавшиеся изменения с указанием причины их внесения.

## <a name="before-you-begin"></a>Подготовка к работе

Рекомендуем документировать следующие сведения:

- **Критерии тестирования.** Определяют контрольные тесты производительности.

- **Компоненты разработки.** Должны быть указаны по меньшей мере в одном критерии тестирования.

Если компонент разработки не присутствует хотя бы в одном критерии тестирования, который соответствует требованию или сценарию, рассмотрите потребность в таком компоненте. Кроме того, убедитесь в наличии следующих элементов:

- **Учетные записи.** Для проверки всех вариантов использования нужны тестовые учетные записи, лицензированные для EMS и Office 365.

- **Устройства.** Тестовые устройства, которые можно очистить или сбросить до заводских настроек.

- **Компоненты интеграции.** Все компоненты интеграции (соединители сертификатов и локальный соединитель Intune Exchange) должны быть установлены и настроены, если это необходимо.

Для преодоления непредвиденных трудностей могут потребоваться изменения в структуре. Кроме того, все изменения структуры следует полностью документировать с указанием причины каждого из них. Ниже приведен пример того, как может выглядеть изменение:

<blockquote>Вы можете осознать, что требования службы регистрации сертификатов для сетевых устройств (NDES) не выполняются, и выяснить, что профили VPN и Wi-Fi можно настроить с помощью корневого ЦС, соответствующего тем же требованиям, без внедрения NDES.</blockquote>

Могут возникнуть проблемы, требующие технической помощи или специализированной диагностики на этапе тестирования и проверки. Рекомендуем обращаться за помощью по каналам технической поддержки Майкрософт.

- [Сведения о получении поддержки для Intune](../get-support.md)

- [Контактные телефоны службы поддержки Microsoft Intune](../get-support.md)

## <a name="functional-validation-testing"></a>Функциональное проверочное тестирование

Функциональная проверка состоит из тестирования каждого компонента, подтверждающего правильность его работы. Проверка проверочного тестирования приведена в таблице ниже.

![Раздел 9, таблица 1](./media/planning-guide-test-validation/section-9-image-1-table.PNG)

## <a name="use-case-validation-testing"></a>Проверочное тестирование вариантов использования

Чтобы убедиться в полноценности и функциональности сценариев, выполните проверочное тестирование вариантов использования. Существуют два типа сценариев вариантов использования — для ИТ-администраторов и для пользователей.

### <a name="it-admin"></a>ИТ-администратор

Проверочное тестирование для ИТ-администратора позволяет убедиться, что административное действие, выполненное для устройства или пользователя, работает правильно. Ниже приведен пример сценария комплексной проверки для ИТ-администратора.

![Раздел 9, таблица 2](./media/planning-guide-test-validation/section-9-image-2-table.PNG)

### <a name="end-user"></a>End user (Конечный пользователь)

Проверочное тестирование для пользователя позволяет убедиться, что взаимодействие с пользователем осуществляется правильно и полноценно. Проверять правильность взаимодействия с конечным пользователем очень важно. Если этого не сделать, изменения могут не прижиться, а нагрузка на службу поддержки вырастет.

![Раздел 9, таблица 3](./media/planning-guide-test-validation/section-9-image-3-table.PNG)

## <a name="next-steps"></a>Дальнейшие шаги

После тестирования и проверки функциональности и сценариев вариантов использования Intune можно приступать к [развертыванию Intune в рабочей среде](../planning-guide-rollout-plan.md).

Дополнительные сведения и шаблоны планирования см. в разделе [дополнительных ресурсов](../planning-guide-resources.md).