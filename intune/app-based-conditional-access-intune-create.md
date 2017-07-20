---
title: "Политика условного доступа на основе приложений в Intune"
description: "Эта статья описывает настройку политики условного доступа на основе приложений в Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a7f054868d0bae061f348239614f3a40b96a15b1
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="set-up-app-based-conditional-access-policies"></a>Настройка политик условного доступа на основе приложений

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Эта статья содержит инструкции по настройке политик условного доступа на основе приложений для приложений, входящих в список утвержденных. В список утвержденных входят приложения, протестированные корпорацией Майкрософт.

> [!IMPORTANT]
> Эта статья описывает шаги по добавлению политики условного доступа на основе приложений с помощью Exchange Online, но вы можете использовать те же действия для добавления других приложений, таких как SharePoint Online, Microsoft Teams и т. д., из списка утвержденных.

## <a name="to-create-an-app-based-conditional-access-policy"></a>Создание политики условного доступа на базе приложений
1.  Откройте [портал Azure](https://portal.azure.com) и войдите с помощью своих учетных данных.

2.  Выберите **Другие службы** и введите "Intune".

3.  Выберите **Защита приложений в Intune**.

4.  В колонке **Управление мобильными приложениями Intune** выберите **Все параметры**.

5.  В разделе **Условный доступ** выберите **Exchange Online**.

    ![Снимок экрана: колонка параметров с разделом условного доступа с выделенным параметром Exchange Online](./media/MAM-conditional-access-1.png)

6. В колонке **Разрешенные приложения** выберите параметр **Разрешить приложения, поддерживающие политики приложений Intune**, чтобы разрешить обращаться к Exchange Online только тем приложениям, которые поддерживаются политиками защиты приложений Intune. При выборе этого параметра отображается список поддерживаемых приложений.

    > [!NOTE]
    > Все почтовые клиенты Exchange Active Sync, включая встроенные почтовые клиенты на iOS и Android, подключающиеся к Exchange Online, не смогут отправлять или получать электронную почту. Вместо этого пользователи получат одно электронное сообщение о том, что им необходимо использовать приложение электронной почты Outlook.

7. Чтобы применить эту политику для пользователей, откройте колонку **Ограниченные группы пользователей** и выберите **Добавить группу пользователей**. Выберите одну или несколько групп пользователей, которым нужно назначить эту политику.

    ![Снимок экрана: колонка ограниченных групп пользователей с выделенным параметром "Добавить группу пользователей"](./media/mam-ca-add-user-group.png)

8. Некоторых пользователей из группы пользователей, выбранной на предыдущем шаге, можно вывести из-под действия этой политики. Для этого нужно добавить группу пользователей в список исключенных групп пользователей. В колонке **Exchange Online** выберите **Исключенные группы пользователей**. Выберите **Добавить группу пользователей**, чтобы открыть список групп пользователей. Выберите группы, которые требуется вывести из-под действия этой политики.

## <a name="to-modify-or-delete-user-groups-from-an-existing-app-based-ca-policy"></a>Изменение групп пользователей или их удаление из существующей политики условного доступа на базе приложения

1. Откройте колонку **Ограниченные группы пользователей**, а затем выделите группу пользователей, которую нужно удалить.
2. Щелкните многоточие, чтобы просмотреть параметры удаления.
3. Выберите **Удалить**, чтобы удалить группу пользователей из списка.

## <a name="next-steps"></a>Дальнейшие действия
[Блокировка приложений, не поддерживающих современные средства проверки подлинности](app-modern-authentication-block.md)

### <a name="see-also"></a>См. также

[Защита данных приложений с помощью политик защиты приложений](app-protection-policies.md)