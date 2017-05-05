---
title: "Портал диагностики службы технической поддержки | Документация Майкрософт"
titleSuffix: Intune Azure preview
description: "Персонал службы технической поддержки использует портал диагностики для устранения технических проблем пользователей"
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 03/18/17
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e0ecc775f70703574c4e1adf0f0aa204f2745b72
ms.openlocfilehash: 723830f686991fe13de13f75c6a5d1bc84e6920b
ms.lasthandoff: 04/20/2017

---
# <a name="help-users-with-the-troubleshooting-portal-in-microsoft-intune"></a>Помогите пользователям устранить проблемы с помощью портала диагностики в Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Портал диагностики позволяет операторам службы технической поддержки и администраторам Intune просматривать пользователей и их устройства и выполнять задачи для решения технических проблем Intune.

## <a name="add-help-desk-operators"></a>Добавление операторов службы технической поддержки
Администратор Intune может назначать пользователям разрешения оператора службы технической поддержки. После этого пользователи службы технической поддержки смогут просматривать портал Intune, но они не смогут просматривать или выполнять административные задачи за пределами рабочей нагрузки по устранению неполадок.

1. Войдите на [портал Azure](https:portal.azure.com) с помощью учетной записи администратора Intune, выберите **Другие службы** > **Мониторинг и управление** > **Intune**.
2. В колонке навигации слева выберите **Роли Intune**.
3. В рабочей нагрузке **Роли Intune** выберите **Оператор службы технической поддержки**, а затем выберите **Назначить**.
4. Введите **Имя назначения** (обязательно), **Описание назначения** (необязательно), а затем назначьте **Участников (группы)** и **Область (группы)**.
5. Участники роли оператора службы технической поддержки теперь могут использовать портал диагностики.

Дополнительные сведения о ролях Intune см. в разделе [Роли Intune (RBAC) для Microsoft Intune](https://docs.microsoft.com/intune-azure/access-control/role-based-access-control).

## <a name="access-the-troubleshooting-portal"></a>Доступ к порталу диагностики

Персонал службы технической поддержки и администраторы Intune могут перейти на портал диагностики двумя способами.
- На [портале Azure](https:portal.azure.com)выберите последовательно **Другие службы** > **Мониторинг и управление** > **Intune**. В колонке навигации слева выберите **Устранение неполадок**. Другие рабочие нагрузки отображаются в колонке навигации слева, но они недоступны.
![Снимок экрана: рабочая нагрузка устранения неполадок Intune со ссылкой "Выбор пользователя"](media/help-desk-user.png)
- Откройте в веб-браузере [http://aka.ms/intunetroubleshooting](http://aka.ms/intunetroubleshooting). Отображается только портал диагностики.

## <a name="use-the-troubleshooting-portal"></a>Использование портала диагностики

На портале диагностики щелкните ссылку **Выбор пользователя**, чтобы просмотреть сведения о пользователях. Сведения о пользователях помогут вам понять текущее состояние пользователей и их устройств. Портал диагностики отображает следующие сведения о пользователях и устройствах Intune.
- Информация об учетной записи пользователя
- Членство пользователя в группе
- Сведения об устройстве

Пользователи службы технической поддержки также могут выполнять на устройствах удаленные задачи, например **удаленную блокировку**.
