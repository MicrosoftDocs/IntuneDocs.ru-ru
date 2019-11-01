---
title: Определение требований для сценариев вариантов использования
titleSuffix: Microsoft Intune
description: Эта статья поможет определить требования к сценариям обычных и второстепенных вариантов использования Intune для внедрения Microsoft Intune с использованием только облачной среды.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: fd8cb5f7-19f0-4d80-8825-2bafa49624af
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7c72cf963822284702f6b924ca506f8ec1157e91
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505139"
---
# <a name="determine-use-case-scenario-requirements"></a>Определение требований для сценариев вариантов использования

В этом разделе вы определите требования для каждой организационной группы в каждом из сценариев вариантов использования. Это поможет вам лучше подготовиться к другим аспектам планирования развертывания Intune, таким как архитектура и проектирование, адаптация и развертывание. Кроме того, эта процедура поможет выявить потенциальные недоработки и проблемы, связанные с проектом развертывания Intune.

Вы можете задать различные наборы требований для каждого из сценариев обычных и второстепенных вариантов использования, а также связанных с ними организационных групп и платформ мобильных устройств. Например, в корпоративном сценарии может требоваться регистрация устройств в Intune с большими ограничениями, например с использованием 6-значного ПИН-кода или отключением резервного копирования в облако. В сценарии с использованием личных устройств (BYOD) ограничения могут быть менее строгими и позволять использовать 4-значный ПИН-код и резервное копирование в облако.

Можно также использовать организационные группы для корпоративного сценария вариантов использования, имеющие другие наборы требований (например, параметры ПИН-кода, профиль Wi-Fi или VPN, развернутые приложения). Требования можно определить по возможностям платформы мобильных устройств (например, сканер отпечатков пальцев, профиль электронной почты).

Ниже приведено несколько примеров для требований к вариантам использования в организации с различными наборами требований для каждого из сценариев обычных и второстепенных вариантов использования, организационных групп и платформ мобильных устройств. Приведенную ниже таблицу можно использовать и для указания требований к вариантам применения в организации:

| **Варианты использования** | **Второстепенные варианты использования** | **Группы** | **Платформы устройств** | **Требования** |
|:---:|:---:|:---:|:---:|:---:|
| Корпоративный | Информационный работник | Отдел кадров, финансы | iOS | Защита электронной почты, параметры устройства, профили, приложения |                                                          
| Корпоративный | Руководители | Отдел кадров, финансы | iOS | Защита электронной почты, параметры устройства, профили, приложения |                                                         
| Корпоративный | Киоск | Розничная торговля | Android | Параметры устройства, профили, приложения |
| BYOD | Информационный работник | Маркетинг, продажи | iOS | Защита электронной почты, параметры устройства, профили, приложения |                                                         
| BYOD | Руководители | Маркетинг, продажи | iOS | Защита электронной почты, параметры устройства, профили, приложения |

Вы можете [скачать шаблон приведенной выше таблицы](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) и использовать его для ввода требований основных и второстепенных вариантов использования для организации.


## <a name="examples-of-requirements"></a>Примеры требований

Вот несколько дополнительных примеров, которые можно использовать в столбце "Требования":

- **Защищенная электронная почта**
  - Условный доступ для локальной организации Exchange или Exchange Online
  - Политики защиты приложений Outlook

- **Параметры устройства**
  - Настройка ПИН-кода с четырьмя или шестью знаками
  - Ограничение резервного копирования в облако

- **Профили**
  - Wi-Fi
  - VPN
  - Электронная почта (Windows 10 Mobile)

- **Приложения**
  - Office 365 с политиками защиты приложений
  - Бизнес-решения с политиками защиты приложений

## <a name="next-steps"></a>Дальнейшие шаги

В следующем разделе приведены рекомендации по [разработке плана развертывания Intune](planning-guide-rollout-plan.md).