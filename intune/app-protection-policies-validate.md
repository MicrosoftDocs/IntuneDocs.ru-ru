---
title: "Проверка политик защиты приложений"
titleSuffix: Intune Azure preview
description: "Предварительная версия Intune Azure. В этом разделе описывается, как можно протестировать и проверить правильность настройки и работы политики защиты приложений."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angerobe
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 15f8a838-0b69-412b-a42e-c6edb61f0cae
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 26e191965eff482cf97b920e028cdf60d1881d32
ms.contentlocale: ru-ru
ms.lasthandoff: 05/23/2017


---

# <a name="how-to-validate-your-app-protection-policy-setup"></a>Проверка настройки политики защиты приложений

[!INCLUDE[azure_preview](./includes/azure_preview.md)]


В этом разделе приведены сведения о поиске неполадок после настройки политики защиты приложений. Это руководство применяется к политикам защиты приложений в **предварительной версии** портала Azure.

### <a name="checking-for-symptoms"></a>Проверка симптомов
Так как защита приложений служит для защиты данных, получение отчетов о неполадках от пользователей маловероятно. При наличии проблемы с конфигурацией защиты приложений пользователь получает неограниченный доступ, как если бы защита приложений полностью отсутствовала, и не имеет представления о том, что возникла проблема. Поэтому рекомендуется проверить конфигурацию защиты приложений с помощью пилотного проекта политик защиты приложений с небольшой группой пользователей, способной преднамеренно испытать ограничения защиты приложений.


### <a name="what-to-check"></a>Проверяемые элементы

Если тестирование показывает, что поведение политики защиты приложений отличается от ожидаемого, рекомендуется проверить следующее:

- Имеют ли пользователи лицензии на защиту приложений?
- Имеют ли пользователи лицензии на O365?
- Состояние каждого из приложений для защиты приложений пользователей. Возможные состояния для приложений: **Записано после изменений** и **Не записано после изменений**.

#### <a name="user-app-protection-status"></a>Состояние защиты приложений пользователя
1. На портале Azure выберите **Управление приложениями** > **Монитор** >  **App protection user status** (Состояние защиты приложений (пользователи)) > **Пользователи**.

2. Выберите пользователя из списка или найдите и выберите его, а затем выберите **Выбор пользователя**. В верхней части столбца **Отчеты по приложению** отображаются сведения о том, есть ли у пользователя лицензия для защиты приложений. Ниже указано, есть ли у него лицензия для O365, а также состояние приложения для всех его устройств.



### <a name="what-to-do"></a>Предпринимаемые действия
Ниже приведены действия, которые выполняются в зависимости от состояния пользователя:

- Если у пользователя нет такой лицензии, назначьте ему лицензию Intune.
- Если пользователь не лицензирован для O365, получите для него лицензию.
- Если для приложения пользователя отображается состояние **Не записано после изменений**, проверьте, правильно ли настроена политика защиты приложений для этого приложения.
- Убедитесь, что эти условия применяются ко всем пользователям, к которым должны применяться политики защиты приложений.

### <a name="see-also"></a>См. также

[What is Intune app protection policy?](app-protection-policies.md) (Что такое политика защиты приложений в Intune?)
