---
title: "Настройка корпоративного портала | Документы Майкрософт"
description: "Корпоративный портал Intune позволяет пользователям выполнять общие задачи, такие как регистрация устройств, установка приложений и поиск сведений об ИТ-отделе."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/14/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: eb4a9f01-f857-4563-ab6f-5d0d7dfa659d
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: b18b3214bc91eed71fc129949532f611cf277d7a
ms.contentlocale: ru-ru
ms.lasthandoff: 05/23/2017


---

# <a name="customize-the-company-portal"></a>Настройка корпоративного портала

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

В этом разделе администраторы узнают, как настроить корпоративный портал Intune и его приложение.

С помощью корпоративного портала Intune пользователи могут обращаться к данным компании и решать общие задачи, такие как регистрация устройств, установка приложений и получение поддержки отдела ИТ.

Корпоративный портал Intune предоставляет пользователям доступ к корпоративным данным и приложениям. Корпоративный портал в двух формах.

-   **Приложение корпоративного портала** — приложение, доступное на устройствах, управляемых с помощью Intune. Узнайте больше о приложениях корпоративного портала для [Android](/intune-user-help/using-your-android-device-with-intune), [iOS](/intune-user-help/using-your-iOS-or-macOS-device-with-intune) и [Windows](/intune-user-help/using-your-windows-device-with-intune).


- **Веб-сайт корпоративного портала** — веб-сайт, позволяющий пользователям выполнять большинство задач, которые можно выполнить из приложения корпоративного портала. URL-адрес корпоративного портала Intune: [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com). Дополнительные сведения об этом веб-сайте см. в статье [Использование веб-сайта корпоративного портала Intune](/intune-user-help/using-the-intune-company-portal-website).

> [!TIP]
> При настройке корпоративного портала все конфигурации применяются к веб-сайту корпоративного портала и приложениям корпоративного портала.

Ниже приведены некоторые задачи, которые пользователи могут выполнять на корпоративном портале.

-   регистрации устройств;
-   просмотра состояния устройств;
-   Сброс настроек устройства
-   Сброс паролей
-   Удаленная блокировка устройства
-   загрузки программного обеспечения, которое развертывается в организации.
-   Обращение в ИТ-отдел за поддержкой

## <a name="customize-company-portal-settings"></a>Настройка параметров корпоративного портала
Настройка корпоративного портала позволяет обеспечить удобную и привычную среду для конечных пользователей. Войдите в [консоль администрирования Microsoft Intune](https://manage.microsoft.com) в качестве администратора клиента или службы, выберите **Администрирование** &gt; **Корпоративный портал** и настройте параметры корпоративного портала.

![admin-console-admin-workspace-comp-portal-settings](./media/companyportal.png)

## <a name="company-contact-information-and-privacy-statement"></a>Контактные данные организации и заявление о конфиденциальности
Название организации отображается в качестве заголовка корпоративного портала. Контактные данные и сведения отображаются для пользователей на экране "Обратиться в ИТ-службу" корпоративного портала. Заявление о конфиденциальности отображается, когда пользователь щелкает ссылку на заявление о конфиденциальности.

|Имя поля|Максимальная длина|Дополнительные сведения|
    |----------|------------------------|----------------|
    |Название организации|40|Это название отображается в качестве заголовка корпоративного портала.|
    |Имя контакта ИТ-отдела|40|Это имя отображается на странице **Обратиться в ИТ-службу**.|
    |Номер телефона ИТ-отдела|20|Этот номер отображается на странице **Обратиться в ИТ-службу**.|
    |Адрес электронной почты ИТ-отдела|40|Этот адрес отображается на странице **Обратиться в ИТ-отдел**. Необходимо ввести допустимый адрес электронной почты в формате **alias@domainname.com**.|
    |Дополнительные сведения|120|Отображается на странице **Обратиться в ИТ-службу**.|
    |URL-адрес заявления о конфиденциальности организации|79|Можно указать собственное заявление компании, которое отображается при выборе ссылок на заявления о конфиденциальности на корпоративном портале. Необходимо ввести допустимый URL-адрес в следующем формате: https://www.contoso.com.|

## <a name="support-contacts"></a>Контактные данные службы поддержки
Адрес веб-сайта поддержки отображается для пользователей на корпоративном портале, позволяя им получить доступ к услугам поддержки через Интернет.

|Имя поля|Максимальная длина|Дополнительные сведения|
    |----------|------------------------|----------------|
    |URL-адрес веб-сайта поддержки|150|Если существует веб-сайт службы поддержки, на который могут обращаться пользователи, укажите его URL-адрес. URL-адрес должен иметь следующий формат: https://www.contoso.com. Если URL-адрес не указан, на странице **Обратиться в ИТ-службу** на корпоративном портале не отображается никаких сведений о веб-сайте.|
    |Имя веб-сайта|40|Это понятное имя, которое отображается для URL-адреса веб-сайта. Если указан URL-адрес, а понятное имя не задано, на странице **Обратиться в ИТ-службу** на корпоративном портале отображается **Перейти на сайт ИТ-отдела**.|

## <a name="company-branding-customization"></a>Настройка фирменной символики организации
Можно настроить корпоративный портал организации, используя ее логотип, название, цвет темы и фоновый рисунок.

|Имя поля|Дополнительные сведения|
    |----------|----------------|
    |Цвет темы|Выберите цвет темы, который будет применен к корпоративному порталу.|
    |Добавить эмблему компании|Если включить этот параметр, можно отправить логотип компании, который будет отображаться на корпоративном портале. Вы можете отправить два логотипа — для белого цвета фона и для цвета выбранной вами темы. Файл логотипа должен быть в формате PNG или JPG и иметь максимальное разрешение 400 x 100 пикселей и размер не более 750 КБ.|
    |"Выберите фон для приложения корпоративного портала Windows 8"|Этот параметр влияет только на фон приложения Корпоративного портала Windows 8.|


Сохранив изменения, можно использовать ссылки, указанные внизу страницы **корпоративного портала** консоли администрирования, чтобы просмотреть веб-сайт корпоративного портала. Эти ссылки нельзя изменить. При входе пользователя в систему эти ссылки отображают подписки в корпоративном портале.

>[!div class="step-by-step"]

>[&larr; **Создание политик и приложений**](.\start-with-a-paid-subscription-to-microsoft-intune-step-6.md) [**Регистрация устройств** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-8.md)  
