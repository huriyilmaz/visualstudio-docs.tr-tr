---
title: Kural koşulu Düzenleyicisi Iletişim kutusu (eski) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleConditionDialog.UI
helpviewer_keywords:
- Rule Condition dialog box
ms.assetid: c7ca8be9-de31-4a64-939c-4d53a50d5e29
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 00df917b05f5073634b0956a0b44e5b0fc6026a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75846327"
---
# <a name="rule-condition-editor-dialog-box-legacy"></a>Kural Koşulu Düzenleyicisi İletişim Kutusu (Eski)
Bu konuda, eski sürümündeki **kural koşulu Düzenleyicisi** iletişim kutusunun nasıl kullanıldığı açıklanmaktadır [!INCLUDE[wfd1](../includes/wfd1-md.md)] . Ya da ' i hedefliyorsanız, eski kullanın [!INCLUDE[wfd2](../includes/wfd2-md.md)] [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 **Kural koşulu Düzenleyicisi** iletişim kutusunu kullanarak bildirime dayalı kural koşulları oluşturun ve değiştirirsiniz. Bu kural koşulları, aşağıdaki Windows Workflow Foundation hazır etkinlikler üzerinde özellikler olarak sunulur:

- [ConditionedActivityGroup](https://msdn2.microsoft.com/library/system.workflow.activities.conditionedactivitygroup.aspx)

- [IfElseBranchActivity](https://msdn2.microsoft.com/library/system.workflow.activities.ifelsebranchactivity.aspx)

- [ReplicatorActivity](https://msdn2.microsoft.com/library/system.workflow.activities.replicatoractivity.aspx)

- [WhileActivity](https://msdn2.microsoft.com/library/system.workflow.activities.whileactivity.aspx)

- [SequentialWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.sequentialworkflowactivity.aspx)

- [StateMachineWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.statemachineworkflowactivity.aspx)

  **Kural koşulu Düzenleyicisi** Iletişim kutusuna [Koşul Seç Iletişim kutusunu (eski)](../workflow-designer/select-condition-dialog-box-legacy.md)kullanarak erişirsiniz.

  Aşağıdaki tabloda, **kural koşulu Düzenleyicisi** iletişim kutusunun kullanıcı ARABIRIMI (UI) öğeleri açıklanmaktadır.

|Arabirim Öğesi|Açıklama|
|----------------|-----------------|
|**Koşul**|Kural koşulunun ifadesini girin.|
|**Tamam**|Kural koşulunu kaydetmek için tıklayın.|

## <a name="entering-condition-expressions"></a>Koşul Ifadelerini girme
 Koşul ifadeleri metin olarak girilir. **Bunu yazabilirsiniz.** bir IntelliSense benzeri bir menü kullanarak iş akışında kullanılan alanlara, özelliklere ve yöntemlere başvurmak için düzenleyiciye. Ya da doğrudan bir iş akışı üye adı yazabilirsiniz. Koşula mantıksal işleçler ekleyebilirsiniz, örneğin ve, veya. Ayrıca, koşullar da ekleyebilirsiniz. Bir koşul, ikili bir işleçtir ve iki işleçtir. Desteklenen ikili işleçler,, **==** ve ' dir **>** **\<**, **>=** **<=** . Desteklenen işlenenler sabit değer, aritmetik işlev ve kapsamlı ortak üyeleridir.

 Karşılaştırma için türü belirtebilir ve **null** ya da boş bir dize ile karşılaştırabilirsiniz. Karmaşık bir tür içeren bir değişkende bulunan üyelere iç içe çağrılar yapabilirsiniz, örneğin, `this.Address.State == "WA"` .

 Kural koşulu Düzenleyicisi aşağıdaki işleçleri destekler:

- İlişkisel işleçler: = =, =,! =

- Karşılaştırma işleçleri: <, \<=, > , >=

- Aritmetik işleçler: +,-, *,/, MOD

- Mantıksal işleçler: ve,  &&, OR,  &#124;&#124;, NOT,!

- Bit düzeyinde işleçler: &, &#124;

  İfade işleci önceliği C# işleç öncelik kurallarını izler.

  Kural koşulu Düzenleyicisi aşağıdaki sayısal ifadeleri destekler:

  this. i = = 1D (1,0 olarak çözümlenir)

  this. i = = 1E1 (10,0 olarak çözümlenir)

  this. i = = 1L (uzun olarak çözümlendi)

  this. i = = 1M (ondalık olarak çözümlenir)

  this. i = = 1F (tek olarak çözümlenir)

  this. i = = 1U (işaretsiz bir int olarak çözümlenir)

  Koşullar hakkında daha fazla bilgi için bkz. [Iş akışlarında koşulları kullanma](https://msdn2.microsoft.com/library/bb628447.aspx).

## <a name="see-also"></a>Ayrıca Bkz.
 [IfElseActivity](https://msdn2.microsoft.com/library/system.workflow.activities.ifelseactivity.aspx) [ConditionedActivityGroup](https://msdn2.microsoft.com/library/system.workflow.activities.conditionedactivitygroup.aspx) [ReplicatorActivity](https://msdn2.microsoft.com/library/system.workflow.activities.replicatoractivity.aspx) [WhileActivity](https://msdn2.microsoft.com/library/system.workflow.activities.whileactivity.aspx) [Koşul Seç iletişim kutusu (eski)](../workflow-designer/select-condition-dialog-box-legacy.md) [Using Conditions in Workflows](https://msdn2.microsoft.com/library/bb628447.aspx) [Kullanıcı arabiriminde eski tasarımcı Windows Workflow Foundation UI Yardımı](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)
