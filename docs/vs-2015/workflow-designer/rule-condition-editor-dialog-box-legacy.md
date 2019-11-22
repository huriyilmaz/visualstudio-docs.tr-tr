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
ms.openlocfilehash: a632b90e89e58c26ec72083fe3f4ed9223826dae
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302856"
---
# <a name="rule-condition-editor-dialog-box-legacy"></a>Kural Koşulu Düzenleyicisi İletişim Kutusu (Eski)
Bu konu başlığı altında, eski [!INCLUDE[wfd1](../includes/wfd1-md.md)]**kural koşulu Düzenleyicisi** iletişim kutusunun nasıl kullanılacağı açıklanmaktadır. Eski kullanın [!INCLUDE[wfd2](../includes/wfd2-md.md)] hedeflemek gerektiğinde [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] veya [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 **Kural koşulu Düzenleyicisi** iletişim kutusunu kullanarak bildirime dayalı kural koşulları oluşturun ve değiştirirsiniz. Bu kural koşulları, aşağıdaki Windows Workflow Foundation hazır etkinlikler üzerinde özellikler olarak sunulur:

- [ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017)

- [IfElseBranchActivity](https://go.microsoft.com/fwlink?LinkID=65034)

- [ReplicatorActivity](https://go.microsoft.com/fwlink?LinkID=65039)

- [WhileActivity](https://go.microsoft.com/fwlink?LinkID=65049)

- [SequentialWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65040)

- [StateMachineWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65045)

  **Kural koşulu Düzenleyicisi** Iletişim kutusuna [Koşul Seç Iletişim kutusunu (eski)](../workflow-designer/select-condition-dialog-box-legacy.md)kullanarak erişirsiniz.

  Aşağıdaki tabloda, **kural koşulu Düzenleyicisi** iletişim kutusunun kullanıcı ARABIRIMI (UI) öğeleri açıklanmaktadır.

|Arabirim Öğesi|Açıklama|
|----------------|-----------------|
|**Koşul**|Kural koşulunun ifadesini girin.|
|**Tamam**|Kural koşulunu kaydetmek için tıklayın.|

## <a name="entering-condition-expressions"></a>Koşul Ifadelerini girme
 Koşul ifadeleri metin olarak girilir. **Bunu yazabilirsiniz.** bir IntelliSense benzeri bir menü kullanarak iş akışında kullanılan alanlara, özelliklere ve yöntemlere başvurmak için düzenleyiciye. Ya da doğrudan bir iş akışı üye adı yazabilirsiniz. Koşula mantıksal işleçler ekleyebilirsiniz, örneğin ve, veya. Ayrıca, koşullar da ekleyebilirsiniz. Bir koşul, ikili bir işleçtir ve iki işleçtir. Desteklenen ikili işleçler **==** , **>** , **\<** , **>=** ve **<=** . Desteklenen işlenenler sabit değer, aritmetik işlev ve kapsamlı ortak üyeleridir.

 Karşılaştırma için türü belirtebilir ve **null** ya da boş bir dize ile karşılaştırabilirsiniz. Karmaşık bir tür içeren bir değişkende (örneğin, `this.Address.State == "WA"`iç içe çağrılar yapabilirsiniz.

 Kural koşulu Düzenleyicisi aşağıdaki işleçleri destekler:

- İlişkisel işleçler: = =, =,! =

- Karşılaştırma işleçleri: <, \<=, >, > =

- Aritmetik işleçler: +,-, *,/, MOD

- Mantıksal işleçler: ve, & &, veya, &#124; &#124;, Not,!

- Bit düzeyinde işleçler: &,&#124;

  İfade işleci önceliği, C# işleç öncelik kurallarını izler.

  Kural koşulu Düzenleyicisi aşağıdaki sayısal ifadeleri destekler:

  this. i = = 1D (1,0 olarak çözümlenir)

  this. i = = 1E1 (10,0 olarak çözümlenir)

  this. i = = 1L (uzun olarak çözümlendi)

  this. i = = 1M (ondalık olarak çözümlenir)

  this. i = = 1F (tek olarak çözümlenir)

  this. i = = 1U (işaretsiz bir int olarak çözümlenir)

  Koşullar hakkında daha fazla bilgi için bkz. [Iş akışlarında koşulları kullanma](https://go.microsoft.com/fwlink?LinkID=65009).

## <a name="see-also"></a>Ayrıca Bkz.
 [IfElseActivity](https://go.microsoft.com/fwlink?LinkID=65033) [ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017) [ReplicatorActivity](https://go.microsoft.com/fwlink?LinkID=65039) [WhileActivity](https://go.microsoft.com/fwlink?LinkID=65049) [Koşul Seç iletişim kutusu (eski)](../workflow-designer/select-condition-dialog-box-legacy.md) [](https://go.microsoft.com/fwlink?LinkID=65009) [Kullanıcı arabiriminde eski tasarımcı Windows Workflow Foundation UI Yardımı](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)