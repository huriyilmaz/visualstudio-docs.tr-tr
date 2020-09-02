---
title: 'Nasıl yapılır: PolicyActivity kural kümesi oluşturma (eski) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- PolicyActivity activity, creating rule sets
- Rule Set Editor dialog box
- PolicyActivity activity, selecting rule sets
- Select Rule Set dialog box
- rule sets, creating for PolicyActivity
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0f8599348d204d149f3e28d17d681941ddf476b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75849326"
---
# <a name="how-to-create-a-policyactivity-rule-set-legacy"></a>Nasıl Yapılır: PolicyActivity Kural Kümesi Oluşturma (Eski)
Bu konuda, veya ' i hedefleyen bir ilke etkinlik kuralı kümesinin nasıl oluşturulacağı açıklanmaktadır [!INCLUDE[wfd1](../includes/wfd1-md.md)] [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 Bir **ilke** etkinlik öğesini **araç kutusundan** iş akışı tasarım yüzeyine sürükledikten sonra, mevcut bir kuralı seçmek veya [PolicyActivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx) etkinliği için yeni bir kural kümesi oluşturmanız gerekir. Kural kümesi [Seç Iletişim kutusunu (eski)](../workflow-designer/select-rule-set-dialog-box-legacy.md) kullanarak varolan bir kural kümesini seçin ve kural [kümesi Düzenleyicisi Iletişim kutusunu (eski)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)kullanarak kural kümeleri oluşturun.

> [!NOTE]
> [Kural kümesi Düzenleyicisi Iletişim kutusu (eski)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) iletişim kutusunu, iş akışı tasarım yüzeyinde bir [PolicyActivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx) etkinliğine çift tıklayarak da açabilirsiniz.

### <a name="to-select-or-create-a-rule-set-for-a-policyactivity-activity"></a>PolicyActivity etkinliğine yönelik bir kural kümesi seçmek veya oluşturmak için

1. [PolicyActivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx)öğesine sağ tıklayın ve ardından **Özellikler penceresini açmak** için **Özellikler** ' e tıklayın.

2. **RuleSetReference** özelliğine tıklayın.

3. Şunlardan birini yapın:

    - **RuleSetReference** üç nokta ( **...]** düğmesine tıklayın ve ardından [kural kümesi Seç iletişim kutusunda (eski)](../workflow-designer/select-rule-set-dialog-box-legacy.md)varolan bir kural kümesini seçin. Daha sonra 10. adıma gidin.

         -veya-

    - Bir kural kümesi için ad yazın. **RuleSetReference** Ellipses **[...]** düğmesine tıklayın ve ardından [kural kümesi Seç iletişim kutusunda](../workflow-designer/select-rule-set-dialog-box-legacy.md) **Düzenle** ' yi seçin (eski).

         -veya-

    - Bir kural kümesi için ad yazın. **RuleSetReference** özelliğini genişletin ve **RuleSet tanımı** özelliğindeki üç nokta **[...]** simgesini seçin.

         [Kural kümesi Düzenleyicisi Iletişim kutusu (eski)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) açılır.

4. Kural kümesi [Düzenleyicisi Iletişim kutusunda (eski)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)kural kümesine yeni bir kural eklemek Için **Kural Ekle** ' ye tıklayın.

5. **Ad**, **Öncelik**ve yeniden **değerleme** özelliklerini girin veya varsayılan değerleri tutun.

6. **Koşul**için metni girin.

7. **Eylemler** ve **Else eylemleri**için metni girin.

8. Başka bir kural eklemek için **Kural Ekle** ' ye tıklayın.

9. İşiniz bittiğinde **Tamam**'a tıklayın.

## <a name="see-also"></a>Ayrıca Bkz.
 [PolicyActivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx) [kural kümesi Seç iletişim kutusu (eski)](../workflow-designer/select-rule-set-dialog-box-legacy.md) [kural kümesi Düzenleyicisi Iletişim kutusu (eski)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) [ilke etkinliği](https://msdn2.microsoft.com/library/bb675229.aspx) [eski iş akışı etkinlikleri](../workflow-designer/legacy-workflow-activities.md)
