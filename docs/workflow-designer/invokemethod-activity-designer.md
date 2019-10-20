---
title: İş Akışı Tasarımcısı-InvokeMethod etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 593ec198cdfdd8acd1967abb046384711e1fa9ac
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650162"
---
# <a name="invokemethod-activity-designer"></a>InvokeMethod Etkinlik Tasarımcısı

**InvokeMethod** Tasarımcısı, bir <xref:System.Activities.Statements.InvokeMethod> etkinliği oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-invokemethod-activity"></a>InvokeMethod etkinliği

@No__t_0, belirtilen nesnenin veya türün ortak bir yöntemini çağırır.

### <a name="use-the-invokemethod-activity-designer"></a>InvokeMethod etkinlik tasarımcısını kullanma

**Araç kutusunun** **temel elemanlar** kategorisindeki **InvokeMethod** etkinlik tasarımcısına erişin. **InvokeMethod** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, bir <xref:System.Activities.Statements.Sequence> içinde olduğu gibi, hiç etkinliğin genellikle yerleştirildiği iş akışı Tasarımcısı yüzeyine bırakılabilir. Etkinlik Tasarımcısı ' nın atılması, InvokeMethod 'un varsayılan <xref:System.Activities.Activity.DisplayName%2A> bir <xref:System.Activities.Statements.InvokeMethod> etkinlik oluşturur. @No__t_0, **InvokeMethod** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-invokemethod-properties"></a>InvokeMethod özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.InvokeMethod> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler özellik kılavuzunda düzenlenebilir ve bazıları İş Akışı Tasarımcısı yüzeyinde düzenlenebilirler.

|Özellik adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|@No__t_0 etkinliğinin kolay adı. Varsayılan değer InvokeMethod ' dır.<br /><br /> @No__t_0 kesinlikle gerekli olmasa da, en iyisi bir tane kullanmaktır.|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|Doğru|Etkinlik yürütüldüğünde çağrılacak yöntemin adı. Çağrılan yöntem **ortak**olarak bildirilmelidir. Bu özellik tasarımcı yüzeyinde düzenlenebilir ve zorunludur.|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|False|Çağrılan metodun parametre koleksiyonu. Parametrelerin, yöntem imzasında göründükleri sırada koleksiyona eklenmesi gerekir. Bu özelliği ayarlayabileceğiniz **Parametreler** iletişim kutusunu göstermek için, özellik kılavuzunun **Parametreler** alanındaki üç nokta düğmesine tıklayın. Parametreleri eklemek için **bağımsız değişken Oluştur** düğmesine tıklayın.|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|False|Yöntem çağrısının dönüş değeri.|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|Doğru|Metodun zaman uyumsuz olarak verilip verilmeyeceğini belirtir. Varsayılan değer **false**'dur.|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|False|Çağrılacak yöntemi içeren nesne. Bu özellik, tasarımcı yüzeyinde düzenlenebilir.<br /><br /> @No__t_0 ya da <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> ayarlanması gerekiyor.|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|False|@No__t_0 türü. Bu özellik tasarımcı yüzeyinde düzenlenebilir. Bu özellik yalnızca çağrılan yöntem static ise ayarlanmalıdır.|

Parametreleri C# **Out** parametresi olarak geçirmek için (örneğin, `Method1(out myParam))` **InOutArgument** yerine **OutArgument** kullanın

**TargetObject** veya **Result** adlı bağımsız değişkenlerle Yöntemler <xref:System.Activities.Statements.InvokeMethod> etkinliği kullanılarak çağrılamaz. Bunun nedeni <xref:System.Activities.Statements.InvokeMethod> etkinliğin <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> ve <xref:System.Activities.Statements.InvokeMethod.Result%2A> <xref:System.Activities.Activity.CacheMetadata%2A> kaydeder.

@No__t_0 parametreleri kaydetme algoritması aşağıdaki listede gösterilmektedir:

1. @No__t_0 bağımsız değişkenini kaydettirin.

2. @No__t_0 bağımsız değişkenini kaydettirin.

3. @No__t_0 koleksiyonunu yineleyin ve her bağımsız değişkeni kaydettirin.

Elde edilen özel durum, şu ileti ile <xref:System.Activities.InvalidWorkflowException> türüdür: ' InvokeMethod ': ' TargetObject ' adlı bir değişken, RuntimeArgument veya DelegateArgument zaten var. Adlar bir ortam kapsamı içinde benzersiz olmalıdır.

Bu kısıtlama <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> ve <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A> için geçerlidir. İş akışı bağımsız değişkenleri değildir ve bu nedenle <xref:System.Activities.Activity.CacheMetadata%2A> yönteminde <xref:System.Activities.Statements.InvokeMethod> etkinliğinin <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> koleksiyonuna kayıtlı değildir.

## <a name="see-also"></a>Ayrıca bkz.

- [Temel Türler](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)