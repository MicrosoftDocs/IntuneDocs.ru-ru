---
title: "Intune Mobile Threat Defense | Документация Microsoft"
description: "Защита доступа к ресурсам организации с учетом риска для устройств."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 08d87906-8158-4d5e-a49d-ad919efef3d1
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 56cd18e1a5556178d951ec47c6e894d8fc2e6f86
ms.contentlocale: ru-ru
ms.lasthandoff: 05/23/2017


---

# <a name="intune-mobile-threat-defense-connectors"></a>Соединители Intune Mobile Threat Defense

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Соединители Intune Mobile Threat Defense позволяют использовать выбранного поставщика Mobile Threat Defense как источник информации для политик соответствия и правил условного доступа. Это позволяет ИТ-администраторам добавить еще один уровень защиты корпоративных ресурсов, например Exchange или Sharepoint, особенно, если дело касается скомпрометированных мобильных устройств.

## <a name="what-problem-does-this-solve"></a>Какие проблемы это решает?

Организациям требуется защищать конфиденциальные данные от новых угроз, включающих физические, основанные на приложениях и сетевые угрозы, а также уязвимости операционной системы.
Сложилось так, что организации действуют с упреждением, когда дело касается защиты компьютеров от атак, но при этом не уделяют должного внимания мониторингу и защите мобильных устройств. Мобильные платформы имеют встроенную защиту, такую как изоляция приложений и проверка приложений для пользователей в магазинах, однако остаются уязвимыми для более сложных атак. Сейчас все больше сотрудников используют устройства для работы и нуждаются в доступе к конфиденциальной информации. Эти устройства нужно защитить от постоянно совершенствующихся атак.

## <a name="how-the-intune-mobile-threat-defense-connectors-work"></a>Принцип работы соединителей Intune Mobile Threat Defense

Соединитель защищает ресурсы компании, создавая канал связи между Intune и выбранным поставщиком Mobile Threat Defense. Партнеры Intune Mobile Threat Defense предлагают интуитивно понятные, простые в развертывании приложения для мобильных устройств, которые активно сканируют и анализируют сведения об угрозах и передают их в Intune для формирования отчетности либо применения правил или политик. Например, если подключенное приложение Mobile Threat Defense сообщает его поставщику о том, что определенный телефон в вашей сети в настоящее время подключен к сети, уязвимой для атак через посредников, эти сведения передаются дальше, относятся к соответствующему уровню риска (низкий, средний или высокий) и сравниваются с допусками, настроенными для уровня риска в Intune — это позволяет определить, следует ли отозвать доступ к определенным ресурсам, если устройство скомпрометировано.

## <a name="sample-scenarios"></a>Примеры сценариев

Если решение Mobile Threat Defense определяет, что устройство заражено:

![Защита мобильных устройств от угроз, зараженное устройство](../media/mtp/MTD-image-1.png)

Доступ предоставляется после того, как устройство будет исправлено:

![Защита мобильных устройств от угроз, доступ предоставлен](../media/mtp/MTD-image-2.png)

## <a name="mobile-threat-defense-partners"></a>Партнеры Mobile Threat Defense

Узнайте, как защитить доступ к ресурсам компании на основе риска для устройства, сети и приложений:

- [Lookout](/intune-classic/deploy-use/lookout-mobile-threat-defense-connector)
- [Skycure](/intune-classic/deploy-use/skycure-mobile-threat-defense-connector)
