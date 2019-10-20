---
title: 'Nasıl yapılır: bildirime dayalı bir kural koşulu oluşturma (eski) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- declarative rule conditions
- condition statements, declarative rule conditions
- Rule Condition Editor dialog box
ms.assetid: 804b6129-c433-408f-a424-46987967730c
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d3a15aad987e46edb58da3560828c70571df2227
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663410"
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>Nasıl yapılır: bildirime dayalı bir kural koşulu oluşturma (eski)
Bu konuda, [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] veya [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] hedefleyen eski [!INCLUDE[wfd1](../includes/wfd1-md.md)] kullanarak bir kural koşulunun nasıl bildirildiği açıklanmaktadır.

 Condition deyiminin **değeri true** veya **false**olarak değerlendirilir. Bildirim temelli bir kural koşulu, [kural koşulu Düzenleyicisi Iletişim kutusu (eski)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) kullanılarak oluşturulan ve iş akışı ile XML olarak depolanan bir koşul deyimidir. Bu, birden çok koşul birleştiren iş akışı durumunu ve Boole ALKU 'ı karşılaştıran koşullar içerebilir.

 Bildirim temelli kural koşulları aşağıdaki Windows Workflow Foundation hazır etkinliklerinde kullanılır:

- [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)

- [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)

- [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)

- [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)

- [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)

- [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)

### <a name="to-create-a-declarative-rule-condition-using-the-rule-condition-editor"></a>Kural koşulu düzenleyicisini kullanarak bildirim temelli bir kural koşulu oluşturmak için

1. Etkinliğin **Özellikler** penceresinde, etkinliğe bağlı olarak **koşul** özelliğine veya **UntilCondition** özelliğine tıklayın.

2. Özellik için listeden **bildirim temelli Kural koşulu** ' nı seçin.

3. **Condition** veya **UntilCondition** özelliğini genişletin.

4. **ConditionName** özelliğine tıklayın.

5. **Koşul Seç** iletişim kutusunu açmak için **ConditionName** üç nokta **[...]** düğmesine tıklayın.

6. **Kural koşulu Düzenleyicisi** iletişim kutusunu açmak Için **Yeni koşul** ' a tıklayın.

7. **Koşul metin kutusuna** koşul için ifadeyi yazın.

     Koşul ifadeleri oluşturma hakkında daha fazla bilgi için bkz. [kural koşulu Düzenleyicisi Iletişim kutusu (eski)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md).

8. Koşul ifadesi oluşturmayı tamamladığınızda, iletişim kutusunu kapatmak için **Tamam** ' a tıklayın ve atanmış bir ada sahip kural koşulunu oluşturun.

     **Koşul Seç** iletişim kutusu açılır.

     **Koşul Seç** iletişim kutusunu kullanma hakkında daha fazla bilgi için bkz. [Koşul Seç Iletişim kutusu (eski)](../workflow-designer/select-condition-dialog-box-legacy.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [While etkinlik](http://go.microsoft.com/fwlink?LinkID=65091) kuralı koşulu Düzenleyicisi iletişim kutusu (eski) kullanılarak [Replicator etkinliğini kullanan](http://go.microsoft.com/fwlink?LinkID=65080) [IfElseBranchActivity etkinliğini](http://go.microsoft.com/fwlink?LinkID=65075) kullanan [eski iş akışı etkinlikleri](../workflow-designer/legacy-workflow-activities.md) [](http://go.microsoft.com/fwlink?LinkID=65066) [ ](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) [Iş akışlarında koşulları kullanarak](http://go.microsoft.com/fwlink?LinkID=65009) [Koşul Seç iletişim kutusu (eski)](../workflow-designer/select-condition-dialog-box-legacy.md)