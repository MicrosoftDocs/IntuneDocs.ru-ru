---
title: "Устранение неполадок с политиками | Документы Майкрософт"
description: "Сведения об устранении неполадок, связанных с конфигурацией политик."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 01/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 99fb6db6-21c5-46cd-980d-50f063ab8ab8
ms.reviewer: tscott
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 91aaf9fb442ecdc43eb7e6ec5ed71a8ead72350c
ms.contentlocale: ru-ru
ms.lasthandoff: 05/23/2017


---

# <a name="troubleshoot-policies-in-microsoft-intune"></a>Устранение неполадок с политиками Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Если у вас возникли проблемы при развертывании политик и управлении ими в Intune, начните здесь. В этой статье описывается ряд распространенных проблем, которые могут возникнуть, а также их решения.

## <a name="general-issues"></a>Общие проблемы

### <a name="was-a-deployed-policy-applied-to-the-device"></a>На устройстве применялась развернутая политика?
**Проблема:** вы не уверены, правильно ли была применена политика.

Для каждого устройства в разделе **Свойства устройства**консоли администрирования Intune имеется вкладка политики. Каждая политика имеет **Предполагаемое значение** и **Состояние**. Предполагаемое значение — это то, чего вы намереваетесь достичь при назначении политики. Состояние — это реальный совокупный результат всех примененных к устройству политик, а также требований и ограничений оборудования и операционной системы. Ниже перечислены возможные состояния:

-   **Соответствует**: устройство получило политику и сообщает службе о соответствии заданному параметру.

-   **Не применимо**: параметр политики не может быть применен. Например, параметры электронной почты для устройств iOS не будут применяться на устройстве Android.

-   **Ожидающие**: политика была отправлена на устройство, однако оно пока не сообщило службе о своем состоянии. Например, для использования шифрования на Android требуется, чтобы конечный пользователь включил функцию шифрования, в результате чего может возникнуть состояние ожидания.

На следующем снимке экрана можно увидеть два понятных примера:

-   Для параметра **Разрешить использование простых паролей** задано значение **Да**, как показано в столбце **Предполагаемое значение**, однако он имеет **Состояние** **Неприменимо**. Это вызвано тем, что простые пароли не поддерживаются для устройств Android.

-   Аналогично, элемент расширенной политики **Параметры электронной почты для устройств iOS** не применяется к этому устройству, так как оно работает под управлением Android.

![Политика устройств Intune](../media/Intune-Device-Policy-v.2.jpg)

> [!NOTE]
> Помните, что при наличии двух политик с разными уровнями ограничений, применимых к одному и тому же устройству или пользователю, используется более строгая политика.


## <a name="issues-with-enrolled-devices"></a>Проблемы с зарегистрированными устройствами

### <a name="alert-saving-of-access-rules-to-exchange-has-failed"></a>Предупреждение: не удалось сохранить правила доступа к Exchange
**Проблема**: в консоли администрирования появляется предупреждение **Не удалось сохранить правила доступа в Exchange**  .

Если вы создали политики в рабочей области политики локальной организации Exchange в консоли администрирования, но используете Office 365, служба Intune не применяет настроенные параметры политики. Обратите внимание на источник политики из предупреждения.  Удалите устаревшие правила в рабочей области политики локальной организации Exchange, так как это глобальные правила Exchange в Intune для локальной организации Exchange, которые не распространяются на Office 365. Затем создайте новую политику для Office 365.

### <a name="cannot-change-security-policy-for-various-enrolled-devices"></a>Не удается изменить политику безопасности для разных зарегистрированных устройств
Устройства Windows Phone не поддерживают последующее снижение уровня безопасности для политик, настроенных с помощью MDM или EAS. Например, вы задали значение 8 для параметра **минимального числа символов в пароле** , а затем хотите уменьшить его до 4. К устройству уже была применена более строгая политика.

Если вы хотите изменить политику на менее безопасную, то в зависимости от платформы устройства может потребоваться выполнить сброс политик безопасности.
Например, на рабочем столе Windows проведите пальцем от правого края, чтобы открыть панель **Чудо-кнопки**, и выберите **Параметры** &gt; **Панель управления**.  Выберите приложение **Учетные записи пользователей** .
В нижней части левого меню навигации находится ссылка **Сбросить политики безопасности** . Выберите ее и нажмите кнопку **Сбросить политики**.
Чтобы применить менее строгие политики для других устройств MDM (например, Android, Windows Phone версии 8.1 и выше, а также iOS), вам, возможно, потребуется прекратить использование и повторно зарегистрировать устройство в службе.

## <a name="issues-with-pcs-that-run-the-intune-software-client"></a>Проблемы с компьютерами под управлением клиентского программного обеспечения Intune

### <a name="microsoft-intune-policy-related-errors-in-policyplatformlog"></a>Ошибки в policyplatform.log, связанные с политиками Microsoft Intune
Для компьютеров Windows под управлением клиентского программного обеспечения Intune ошибки политик в файле policyplatform.log могут быть вызваны тем, что параметрам контроля учетных записей Windows (UAC) на устройстве присвоены значения, отличные от стандартных. Некоторые отличные от используемых по умолчанию значения параметров UAC могут затрагивать установки клиента Microsoft Intune и выполнение политик.

#### <a name="to-resolve-uac-issues"></a>Устранение проблем с UAC

1.  Снимите компьютер с учета, как описано в статье [Снятие устройств с учета в Microsoft Intune](/intune-classic/deploy-use/retire-devices-from-microsoft-intune-management).

2.  Подождите 20 минут для удаления клиентского программного обеспечения.

    > [!NOTE]
    > Не пытайтесь удалить клиент из раздела "Программы и компоненты".

3.  Введите **UAC** в меню "Пуск", чтобы открыть параметры контроля учетных записей.

4.  Переместите ползунок уведомлений на значение по умолчанию.

### <a name="error-cannot-obtain-the-value-from-the-computer-0x80041013"></a>ОШИБКА. Не удается получить значение от компьютера, 0x80041013
Это может произойти в случае, если рассинхронизация времени на локальной системе составляет пять минут или более. В случае рассинхронизации времени на локальном компьютере безопасные транзакции завершаются ошибкой из-за недопустимых меток времени.

Чтобы устранить эту проблему, установите время локальной системы как можно ближе ко времени в Интернете или времени, установленному на контроллерах домена в сети.








### <a name="next-steps"></a>Дальнейшие шаги
Если эта информация не помогла, обратитесь в службу поддержки Майкрософт, как описано в статье [Получение поддержки для Microsoft Intune](how-to-get-support-for-microsoft-intune.md).
