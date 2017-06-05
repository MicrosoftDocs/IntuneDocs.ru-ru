---
title: "Защита Skype для бизнеса Online | Документы Майкрософт"
description: "Защита и контроль доступа к Skype для бизнеса Online с помощью условного доступа."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1b2d7125-f63f-43cf-ac1e-94fbedf2a7e8
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 46dc5bc7d7b4107b87a41aa8a454453d591d0ef9
ms.contentlocale: ru-ru
ms.lasthandoff: 05/23/2017


---

# <a name="protect-access-to-skype-for-business-online-with-microsoft-intune"></a>Защита доступа к Skype для бизнеса Online при помощи Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Вы можете использовать политику условного доступа для **Skype для бизнеса Online**, чтобы управлять доступом к Skype для бизнеса Online.
Условный доступ состоит из двух компонентов:
- Политика соответствия устройств, которой устройства должны удовлетворять, чтобы считаться соответствующими.
- Политика условного доступа, где указываются условия, которым должно удовлетворять устройство для доступа к службе.
Дополнительные сведения о принципах работы условного доступа см. в статье [Защита доступа к электронной почте и службам Office 365](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).

Когда целевой пользователь пытается подключиться к Skype для бизнеса Online на устройстве, выполняется следующая оценка:

![Схема, показывающая точки принятия решений, которые используются для определения того, разрешен ли устройству доступ к Skype для бизнеса Online](../media/ConditionalAccess_SkypeforBusiness.png)

**Перед** настройкой политики условного доступа для Skype для бизнеса Online необходимо выполнить следующие условия:
- Получить **подписку Skype для бизнеса Online** и назначить лицензии Skype для бизнеса Online пользователям.
- Получить **подписку Enterprise Mobility + Security (EMS)** или **Azure Active Directory (Azure AD) Premium** и предоставить пользователям лицензии для EMS или Azure AD. Дополнительные сведения см. в статье [Цены на Enterprise Mobility](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing) или [Цены на Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).

-   [Включение современной проверки подлинности](/intune-classic/deploy-use/restrict-access-to-skype-for-business-online-with-microsoft-intune) для Skype для бизнеса Online.
-  Все пользователи должны использовать **Skype для бизнеса Online**. Если имеется развертывание Skype для бизнеса Online и локальной версии Skype для бизнеса, политика условного доступа для пользователей не применяется.

Устройство, которому требуется доступ к Skype для бизнеса Online должно соответствовать следующим условиям:

-   Устройство должно относиться к платформе **Android** или **iOS**.

-   Оно должно быть **зарегистрировано** в Intune.

-   Оно должно **соответствовать требованиям** всех развернутых политик соответствия требования Intune.


Состояние устройства хранится в службе Azure Active Directory, которая предоставляет или блокирует доступ на основе указанных условий.

Если условие не выполняется, при входе пользователь получает одно из следующих сообщений:

-   Если устройство не зарегистрировано в Intune либо в Azure Active Directory, выводится сообщение с инструкциями о том, как установить приложение корпоративного портала и выполнить регистрацию.

-   Если устройство не соответствует требованиям, отображается сообщение, направляющее пользователя на веб-сайт или в приложение Корпоративного портала Intune, где можно найти сведения об этой проблеме и способах ее решения.

## <a name="configure-conditional-access-for-skype-for-business-online"></a>Настройка условного доступа для Skype для бизнеса Online

### <a name="step-1-configure-azure-active-directory-security-groups"></a>Шаг 1. Настройка групп безопасности Azure Active Directory
Прежде чем начать, настройте политику условного доступа в группах безопасности Azure Active Directory. Эти группы можно настроить в **Центре администрирования Office 365**. Они будут использоваться для назначения пользователей политике или исключения их из нее. Если на пользователя распространяется действие политики, каждое используемое им устройство должно соответствовать этой политике, чтобы он мог получить доступ к ресурсам.

Для политики Skype для бизнеса можно указать два типа групп:

-   **Целевые группы** — группы пользователей, к которым применяется политика.

-   **Исключенные группы** — группы пользователей, которые исключены из политики.

Если пользователь входит в обе группы, то он будет исключен из политики.

### <a name="step-2-configure-and-deploy-a-compliance-policy"></a>Шаг 2. Настройка и развертывание политики соответствия требованиям
[Создайте](create-a-device-compliance-policy-in-microsoft-intune.md) и [разверните](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md) политику соответствия для всех устройств, которые будет затрагивать эта политика. Это все устройства, которые используются пользователями в **целевых группах**.

> [!NOTE]
> Политики соответствия развертываются в группах Intune, тогда как политики условного доступа нацелены на группы безопасности Azure Active Directory.


> [!IMPORTANT]
> Если политика соответствия не развернута, устройства считаются соответствующими.

Когда будете готовы, перейдите к **шагу 3**.

### <a name="step-3-configure-the-skype-for-business-online-policy"></a>Шаг 3. Настройка политики Skype для бизнеса Online
Далее настройте в политике требование, разрешающее доступ к Skype для бизнеса Online только для управляемых и соответствующих политике устройств. Эта политика будет храниться в Azure Active Directory.

1.  В [консоли администрирования Microsoft Intune](https://manage.microsoft.com) выберите **Политика** > **Условный доступ** > **Политика Skype для бизнеса Online**.

  ![Снимок экрана со страницей политики условного доступа Skype для бизнеса Online](./media/conditional_access_SFBPolicy.png)

2.  Выберите параметр **Включить политику условного доступа**.

3.  В разделе **Доступ приложения**  можно выбрать область применения политики условного доступа:

    -   **iOS**

    -   **Android**

4.  В разделе **Целевые группы** нажмите кнопку **Изменить**, чтобы выбрать группы безопасности Azure Active Directory, к которым будет применена политика. В качестве целевой аудитории можно выбрать всех пользователей или отдельные группы пользователей.

5.  Дополнительно в разделе **Исключенные группы** можно нажать кнопку **Изменить**, чтобы выбрать группы безопасности Azure Active Directory, которые будут исключены из этой политики.

6.  По окончании нажмите кнопку **Сохранить**.

Настройка условного доступа для Skype для бизнеса Online выполнена. Развертывать политику условного доступа не нужно, она вступает в силу немедленно.


## <a name="monitor-the-compliance-and-conditional-access-policies"></a>Мониторинг соответствия и политик условного доступа
В рабочей области **Группы** вы можете просмотреть состояние условного доступа своих устройств.

Выберите любую группу мобильных устройств. Затем на вкладке **Устройства** выберите один из следующих **фильтров**:

* **Устройства, не зарегистрированные в AAD** — для этих устройств заблокирован доступ к Skype для бизнеса Online.

* **Устройства, не соответствующие условиям** — для этих устройств заблокирован доступ к Skype для бизнеса Online.

* **Устройства, соответствующие условиям и зарегистрированные в AAD** — эти устройства могут получить доступ к Skype для бизнеса Online.
