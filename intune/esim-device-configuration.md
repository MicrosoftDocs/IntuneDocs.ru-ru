---
title: Включение подключений к данным eSIM в Microsoft Intune — Azure | Документы Майкрософт
description: Добавление или использование eSIM для получения доступа к данным и Интернету с помощью разных тарифных планов. В Intune можно добавить или импортировать коды активации, а затем назначить эти коды активации с помощью профиля конфигурации. Вы также можете отслеживать профили eSIM и проверять состояние устройств с поддержкой eSIM.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 7/31/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 45d41f02fdfff7179dbd43f4d2afdac3337f8b7f
ms.sourcegitcommit: e8aaa0955d13fa6c9d5f35a730ad06509ce88d0b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2018
ms.locfileid: "39400289"
---
# <a name="configure-esim-cellular-profiles-in-intune---public-preview"></a>Настройка профилей сотовой связи eSIM в Intune (общедоступная предварительная версия)

> [!NOTE]
> Нам интересно ваше мнение. Отправьте вопросы или начните обсуждение по электронной почте (`eSIMonIntune@microsoft.com`).

## <a name="introduction"></a>Введение

eSIM — встроенная SIM-карта, которая позволяет подключаться к Интернету через функцию передачи данных по сотовой сети на устройстве с поддержкой eSIM, таком как [Surface LTE Pro](https://www.microsoft.com/surface/business/surface-pro). С eSIM не нужно получать SIM-карту у своего оператора мобильной связи. Пользователи, путешествующие по всему миру, могут также переключаться между мобильными операторами и тарифными планами и всегда оставаться на связи.

Предположим, у вас есть тарифный план сотовой связи для работы и еще один тарифный план другого мобильного оператора для личного пользования. В командировке вы можете получить доступ к Интернету через операторов мобильной связи с тарифными планами в этом регионе.

В Intune можно импортировать одноразовые коды активации, предоставленные оператором мобильной связи. Чтобы настроить тарифные планы сотовой связи в модуле eSIM, разверните эти коды активации на устройстве с поддержкой eSIM. Когда Intune устанавливает код активации, аппаратный модуль eSIM использует данные в коде активации для связи с оператором мобильной связи. После завершения этого процесса профиль eSIM загружается на устройство и настраивается для активации сотовой связи.

Чтобы развернуть eSIM на устройствах с помощью Intune, требуется следующее:

- **Устройства, поддерживающие eSIM**, такие как Surface LTE. Проверьте, [поддерживает ли ваше устройство eSIM](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data). Также см. список [некоторых известных устройств, поддерживающих eSIM](#esim-capable-devices) (в этой статье).
- **Компьютер с Windows 10 Fall Creators Update** (1709 или более поздней версии), который зарегистрирован в Intune и к которому применяется управление мобильными устройствами Intune.
- **Коды активации**, предоставляемые вашим оператором мобильной связи. Эти одноразовые коды активации добавляются в Intune и развертываются на ваших устройствах, поддерживающих eSIM. Коды активации eSIM можно получить у оператора мобильной связи.

## <a name="deploy-esim-to-devices---overview"></a>Развертывание eSIM на устройствах. Обзор

Для развертывания eSIM на устройствах администратор выполняет следующие задачи:

1. импортирует коды активации, предоставляемые вашим оператором мобильной связи;
2. создает группу устройств Azure Active Directory (Azure AD), которая включает ваши устройства, поддерживающие eSIM;
3. назначает группы Azure AD пулу импортированных подписок;
4. отслеживает развертывание.

Эта статья поможет вам выполнить эти процедуры.

## <a name="esim-capable-devices"></a>Устройства, поддерживающие eSIM

Для перечисленных ниже устройств заявлена поддержка eSIM. Кроме того, вы можете проверить, [поддерживает ли ваше устройство eSIM](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data).

- Acer Swift 7
- Asus NovoGo TP370QL
- Asus TP401
- Asus Transformer Mini T103
- HP Elitebook G5
- HP Envy x2
- HP Probook G5
- Lenovo Miix 630
- Lenovo T480
- Samsung Galaxy Book
- Surface Pro LTE

## <a name="step-1-add-cellular-activation-codes"></a>Шаг 1. Добавление кодов активации сотовой связи

Коды активации сотовой связи предоставляются оператором мобильной связи в виде файла с разделителями-запятыми (CSV). Если у вас есть этот файл, добавьте его в Intune, выполнив следующие действия.

1. Войдите на [портал Azure](https://portal.azure.com/).
2. Выберите **Все службы**, отфильтруйте список по **Intune** и выберите **Microsoft Intune**.
3. Выберите **Конфигурация устройства** > **Профили сотовой связи eSIM** > **Добавить**.
4. Выберите CSV-файл с кодами активации.
5. Нажмите кнопку **OK**, чтобы сохранить изменения.

#### <a name="csv-file-requirements"></a>Требования к CSV-файлу

При работе с CSV-файлом с кодами активации убедитесь, что выполняются следующие требования.

- Файл должен быть в формате CSV (filename.csv).
- Структура файла должна соответствовать строгому формату. В противном случае возможен сбой импорта. Intune проверяет файл при импорте, и операция завершается сбоем, если найдены ошибки.
- Коды активации используются один раз. Не рекомендуется импортировать коды активации, которые были импортированы ранее, так как это может вызвать проблемы при развертывании на том же или другом устройстве.
- Каждый файл содержит коды строго для одного оператора мобильной связи, и все коды активации соответствуют одному тарифному плану. Intune распределяет коды активации на целевые устройства случайным образом. Нет никаких гарантий, что устройство получит конкретный код активации.
- В одном CSV-файле можно импортировать максимум 1000 кодов активации.

#### <a name="csv-file-example"></a>Пример CSV-файла

1. Первая строка и первая ячейка CSV-файла — URL-адрес службы активации eSIM оператора мобильной связи, которая называется SM-DP+ (сервер Subscription Manager Data Preparation). URL-адрес должен быть полным доменным именем (FQDN) без запятых.
2. Вторая и все последующие строки — уникальные одноразовые коды активации, которые включают два значения:

    1. первый столбец — это уникальный ICCID (идентификатор SIM-карты);
    2. второй столбец — идентификатор сопоставления с разделителем-запятой (запятая в конце отсутствует). См. следующий пример.

        ![Пример CSV-файла кодов активации оператора мобильной связи](./media/esim-device-configuration/url-activation-code-examples.png)

3. Имя CSV-файла становится именем пула сотовых подписок на портале Azure. На предыдущем рисунке имя файла — `UnlimitedDataSkynet.csv`. Соответственно, имя, присвоенное Intune пулу подписок `UnlimitedDataSkynet.csv`:

    ![Имя пула сотовых подписок соответствует имени примера CSV-файла кодов активации](./media/esim-device-configuration/subscription-pool-name-csv-file.png)

## <a name="step-2-create-an-azure-ad-device-group"></a>Шаг 2. Создание группы устройств Azure AD

Создайте группу устройств, которая включает устройства, поддерживающие eSIM. Процедура приведена в разделе [Добавление групп](groups-add.md).

> [!NOTE]
> - Нацеливание возможно только для устройств, но не для пользователей.
> - Мы рекомендуем создать статическую группу устройств Azure AD, которая включает устройства eSIM. Использование группы гарантирует нацеливание только на устройства eSIM.

## <a name="step-3-assign-esim-activation-codes-to-devices"></a>Шаг 3. Назначение кодов активации eSIM устройствам

Назначьте профиль группе Azure AD, включающей ваши устройства eSIM.

1. На [портале Azure](https://portal.azure.com/) выберите **Все службы**, отфильтруйте список по **Intune** и выберите **Microsoft Intune**.
2. Выберите **Конфигурация устройства** > **Сотовая связь eSIM** > **Профили**.
3. В списке профилей выберите нужный пул сотовых подписок eSIM, а затем нажмите **Назначения**.
4. Выберите **Включить** или **Исключить**, а затем выберите группы.

    ![Включение группы устройств для назначения профиля](./media/esim-device-configuration/include-exclude-groups.png)

5. При выборе групп вы выбираете группу Azure AD. Чтобы выбрать несколько групп, используйте клавишу **CTRL**.
6. Наконец нажмите **Сохранить**.

Коды активации eSIM используются один раз. После установки кода активации на устройстве модуль eSIM обращается к оператору мобильной связи, чтобы загрузить профиль сотовой связи. Эта операция завершается регистрацией устройства в сети оператора мобильной связи.

## <a name="step-4-monitor-deployment"></a>Шаг 4. Мониторинг развертывания

#### <a name="review-the-deployment-status"></a>Проверка состояния развертывания

После назначения профиля можно отслеживать состояние развертывания пула подписок.

1. Войдите на [портал Azure](https://portal.azure.com/).
2. Выберите **Все службы**, отфильтруйте список по **Intune** и выберите **Microsoft Intune**.
3. Выберите **Конфигурация устройства** > **Профили сотовой связи eSIM**. Будет выведен список всех существующих пулов сотовых подписок eSIM.
4. Выберите подписку и просмотрите **состояние развертывания**.

#### <a name="check-the-profile-status"></a>Проверка состояния профиля
После создания профиля устройства вы можете использовать графические схемы Intune. Эти схемы отображают состояние профиля со сведениями о наличии успешно назначенных устройств или конфликтах.

1. Выберите **Конфигурации устройства** > **Профили сотовой связи eSIM** > выберите существующую подписку.
2. На вкладке **Обзор** в верхней диаграмме отображается количество устройств, назначенных определенному развертыванию пула сотовых подписок eSIM.

    Также вы здесь увидите число устройств под управлением других платформ, которым назначен тот же профиль устройства.

    Intune показывает состояние доставки и установки для кодов активации, предназначенных для устройств.

    - **Устройство не синхронизировано**. Целевое устройство не обращалось к Intune с момента создания политики развертывания eSIM.
    - **Ожидается активация**. Временное состояние, когда Intune активно устанавливает код активации на устройстве.
    - **Активно**. Код активации успешно установлен.
    - **Сбой активации**. Не удалось установить код активации (см. руководство по устранению неполадок).

#### <a name="view-the-detailed-device-status"></a>Просмотр подробных сведений о состоянии устройства

Вы можете отслеживать и просматривать подробный список устройств в разделе "Состояние устройства".**

1. Выберите **Конфигурации устройства** > **Профили сотовой связи eSIM** > выберите существующую подписку.
2. Выберите **Состояние устройства**. Intune выведет дополнительные сведения об устройстве.

  - **Имя устройства** — имя целевого устройства.
  - **Пользователь** — пользователь зарегистрированного устройства.
  - **ICCID** — уникальный код, предоставленный оператором мобильной связи в коде активации, установленном на устройстве.
  - **Состояние активации** — состояние доставки и установки кода активации на устройстве.
  - **Состояние сотовой сети** — состояние, предоставленное самим мобильным оператором. Для устранения неполадок обратитесь к оператору мобильной связи.
  - **Последняя запись после изменения** — дата последнего сеанса связи Intune с устройством.

#### <a name="monitor-esim-profile-details-on-the-actual-device"></a>Отслеживание сведений профиля eSIM на фактическом устройстве

1. На вашем устройстве откройте **Параметры** и перейдите в раздел **Сеть и Интернет**.
2. Выберите **Сотовая связь** > **Управление профилями eSIM**.
3. Откроется список профилей eSIM:

    ![Просмотр профилей eSIM в настройках устройства](./media/esim-device-configuration/device-settings-cellular-profiles.png)

## <a name="remove-the-esim-profile-from-device"></a>Удаление профиля eSIM с устройства

При удалении устройства из группы Azure AD профиль eSIM также удаляется. Обязательно сделайте следующее:

1. Убедитесь, что вы используете группу Azure AD с устройствами eSIM.
2. Перейдите к группе Azure AD и удалите устройство из группы.
3. Когда удаленное устройство свяжется с Intune, произойдет оценка измененной политики и удаление профиля eSIM.

Профиль eSIM также удаляется, если пользователь отменяет регистрацию устройства или если на устройстве выполняются удаленные операции [удаления данных компании](devices-wipe.md#remove-company-data) или [сброса устройства](devices-wipe.md#factory-reset).

> [!NOTE]
> Удаление профиля не прекращает выставление счетов автоматически. Обратитесь к оператору мобильной связи, чтобы проверить состояние выставления счетов для вашего устройства.

## <a name="best-practices--troubleshooting"></a>Рекомендации и устранение неполадок

- Убедитесь, что CSV-файл имеет правильный формат. Убедитесь, что файл не содержит повторяющиеся коды, не включает несколько операторов мобильной связи или разные тарифные планы. Помните, что для разных операторов мобильной связи и тарифных планов должны использоваться уникальные файлы.
- Создайте статическую группу устройств Azure AD, которая будет включать только целевые устройства eSIM.
- Если возникла проблема с состоянием развертывания, обратите внимание на следующие факторы.
  - **Ненадлежащий формат файла** — сведения о правильном формате файла см. в разделе **Шаг 1. Добавление кодов активации сотовой связи** этой статьи.
  - **Сбой активации мобильной связи, обратитесь к оператору мобильной связи** — возможно, код активации не активирован в сети оператора. Также возможны ошибки активации мобильной связи и сбой загрузки профиля.

## <a name="next-steps"></a>Дальнейшие шаги
[Настройка профилей устройств](device-profiles.md)