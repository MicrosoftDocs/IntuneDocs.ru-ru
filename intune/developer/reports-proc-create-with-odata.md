---
title: Создание отчета Intune из веб-канала OData с помощью Power BI
titleSuffix: Microsoft Intune
description: Узнайте, как создать визуализацию в виде дерева с помощью Power BI Desktop, используя интерактивный фильтр из API хранилища данных Intune.
keywords: Хранилище данных Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/15/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: A2C8A336-29D3-47DF-BB4A-62748339391D
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: d00ae284ff4ea911cecb571cfe765eafe32fac02
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72490478"
---
# <a name="create-an-intune-report-from-the-odata-feed-with-power-bi"></a>Создание отчета Intune из веб-канала OData с помощью Power BI

В этой статье объясняется, как создать диаграмма дерева визуализацию данных Intune с помощью Power BI Desktop, которые пользователи используют в интерактивном фильтре. Например, вашему финансовому директору может быть необходимо понять, как общее распределение устройств сравнивается с устройствами, принадлежащими компании, и личными устройствами. Диаграмма "дерево" позволяет получить информацию об общем количестве устройств разных типов. Вы можете узнать число корпоративных или личных устройств на основе iOS, Android и Windows.

## <a name="overview-of-creating-the-chart"></a>Общие сведения о создании диаграммы

Чтобы создать эту диаграмму, выполните указанные ниже действия.
1. Установите приложение Power BI Desktop, если у вас его еще нет.
2. Подключитесь к модели хранилища данных Intune и получите актуальные данные для нее.
3. Создайте или настройте связи внутри модели данных.
4. Создайте диаграмму на основе данных из таблицы **devices**.
5. Создайте интерактивный фильтр.
6. Просмотрите готовую диаграмму.

### <a name="a-note-about-tables-and-entities"></a>Замечание касательно таблиц и сущностей

В Power BI вы работаете с таблицами. Таблица содержит поля данных. Каждое поле данных имеет определенный тип. Поле может содержать данные только этого типа. К типам данных относятся числовой тип, текст, даты и т. д. Таблицы в Power BI заполняются текущими данными из клиента при загрузке модели. Хотя данные со временем меняются, структура таблицы остается неизменной, пока вы не измените базовую модель данных.

Не следует путать термины *сущность* и *таблица*. Модель данных доступна через веб-канал OData (Open Data Protocol). Контейнеры, которые в Power BI называются таблицами, в контексте OData называются сущностями. Оба этих термина обозначают один и тот же объект, который служит для хранения данных. Дополнительные сведения о OData см. в [обзоре OData](/odata/overview).

## <a name="install-power-bi-desktop"></a>Установка Power BI Desktop

Установите последнюю версию Power BI Desktop. Ее можно скачать с сайта: [PowerBI.microsoft.com](https://powerbi.microsoft.com/desktop).

## <a name="connect-to-the-odata-feed-for-the-intune-data-warehouse-for-your-tenant"></a>Подключение к веб-каналу OData для хранилища данных Intune вашего клиента

> [!Note]  
> В Intune требуется разрешение **Отчеты**. Дополнительные сведения см. в разделе [Авторизация](../reports-api-url.md).

1. Войдите в [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Откройте панель **Хранилище данных Intune**, щелкнув ссылку на хранилище данных в разделе **Другие задачи** в правой части колонки **Microsoft Intune — Обзор**.
3. Скопируйте настраиваемый URL-адрес веб-канала. Пример: `https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=beta`
4. Откройте Power BI Desktop.
5. В строке меню выберите **файл**  > **получить данные**  > **веб-канал OData**.
6. Вставьте URL-адрес пользовательского канала, скопированный на предыдущем шаге, в поле URL-адрес в окне **канала OData** .
7. Установите переключатель в положение **Основной**.

    ![Веб-канал OData для хранилища данных Intune на вашем клиенте](./media/reports-proc-create-with-odata/reports-create-01-odatafeed.png)

8. Нажмите кнопку **ОК**.
9. Выберите пункт **Учетная запись организации**, а затем выполните вход, используя учетные данные Intune.

    ![Учетные данные организации](./media/reports-proc-create-with-odata/reports-create-02-org-account.png)

10. Выберите **Подключиться**. Откроется окно "Навигатор" со списком таблиц, имеющихся в хранилище данных Intune.

    ![Снимок экрана окна "Навигатор": список таблиц в хранилище данных](./media/reports-proc-create-with-odata/reports-create-02-loadentities.png)

11. Выберите таблицы **devices** и **ownerTypes**.  Выберите **Загрузить**. Power BI загрузит данные в модель.

## <a name="create-a-relationship"></a>Создание связи

Вы можете импортировать несколько таблиц, чтобы проанализировать связанные данные из них. В Power BI есть функция **автообнаружения**, которая пытается автоматически выявить и создать связи. Таблицы в Data Warehouse были созданы так, чтобы поддерживать функцию автообнаружения в Power BI. Но даже если Power BI не удается автоматически найти связи, вы можете настроить их вручную.

![Управление связями связанных данных по таблицам](./media/reports-proc-create-with-odata/reports-create-03-managerelationships.png)

1. Выберите **Управление связями**.
2. Если приложение Power BI еще не обнаружило связи, нажмите кнопку **Автообнаружение...** .

Связи отображаются в столбцах "Из таблицы" и "В таблицу". В этом примере поле данных **ownerTypeKey** в таблице **devices** связано с полем данных **ownerTypeKey** в таблице **ownerTypes**. С помощью этой связи можно определить обычное название по коду типа устройства в таблице **devices**.

## <a name="create-a-treemap-visualization"></a>Создание визуализации в виде дерева

На диаграмме "дерево" данные упорядочены иерархически в виде полей в полях. Каждая ветвь иерархии представляет собой поле, которое содержит поля меньшего размера, представляющие подветви. Вы можете использовать Power BI Desktop для создания диаграмма дерева данных клиента Intune, которые показывают относительные объемы типов изготовителей устройств.

![Визуализация диаграммы дерева в Power BI](./media/reports-proc-create-with-odata/reports-create-03-treemap.png)

1. В области **визуализации** найдите и выберите **Диаграмма дерева**. Диаграмма **Диаграмма дерева** будет добавлена на холст отчета.
2. В области **поля** найдите таблицу `devices`.
3. Разверните таблицу `devices` и выберите `manufacturer` поле данных.
4. Перетащите поле данных `manufacturer` на холст отчета и поместите его на диаграмму **Диаграмма дерева** .
5. `devices` Перетащите поле данных из таблицы на панель **визуализация** и поместите его в разделе **Ценности** в поле **Добавить поля данных**. `deviceKey`  

Вы создали визуализацию, на которой представлено распределение устройств в организации по производителям.

![Диаграмма "дерево" с данными: распределение по производителям устройств](./media/reports-proc-create-with-odata/reports-create-06-treemapwdata.png)

## <a name="add-a-filter"></a>Добавление фильтра

Вы можете добавить к диаграмме "дерево" фильтр, который позволяет получать ответы на дополнительные вопросы.

1. Чтобы добавить фильтр, щелкните холст отчетов, а затем на панели **Визуализации** щелкните **значок среза** (![Диаграмма "дерево" с моделью данных и поддерживаемыми связями](./media/reports-proc-create-with-odata/reports-create-slicer.png)). На холсте отобразится пустая визуализация **среза** .
2. В области **поля** найдите таблицу `ownerTypes`.
3. Разверните таблицу `ownerTypes` и выберите `ownerTypeName` поле данных.
4. `ownerTypes` Перетащите поле данных из таблицы на панель **Фильтры** и поместите его в разделе **Фильтры на этой странице** в поле **Добавить поля данных**. `onwerTypeName`  

   В таблице `OwnerTypes` поле данных с именем `OwnerTypeKey`that содержит данные о том, является ли устройство корпоративным или личным. Так как в фильтре должны отображаться понятные имена, найдите таблицу `ownerTypes` и перетащите поле **ownerTypeName** в срез. Этот пример показывает, как модель данных поддерживает связи между таблицами.

![Диаграмма "дерево" с фильтром: поддерживает связи между таблицами](./media/reports-proc-create-with-odata/reports-create-08_ownertype.png)

Теперь у вас есть интерактивный фильтр, с помощью которого можно переключаться между корпоративными и личными устройствами. Используйте этот фильтр для отслеживания изменений распределения.

1. Выберите **компания** в срезе, чтобы убедиться, что распространение устройств, принадлежащих компании.
2. Выберите **личное** в срезе, чтобы просмотреть персональные устройства.

## <a name="next-steps"></a>Дальнейшие шаги

- Дополнительные сведения о [создании связей и управлении ими](https://powerbi.microsoft.com/documentation/powerbi-desktop-create-and-manage-relationships/) в приложении Power BI Desktop см. в документации по Power BI.
- Изучите [модель хранилища данных Intune](reports-ref-data-model.md).