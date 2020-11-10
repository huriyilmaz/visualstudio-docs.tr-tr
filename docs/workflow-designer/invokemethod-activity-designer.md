---
title: İş Akışı Tasarımcısı-InvokeMethod etkinlik Tasarımcısı
description: InvokeMethod etkinliği ve bir InvokeMethod etkinliği oluşturmak ve yapılandırmak için InvokeMethod etkinlik Tasarımcısı ' nı nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 55162def18d2295e0767a3999ffde75d71e1233d
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437742"
---
# <a name="invokemethod-activity-designer"></a>InvokeMethod Etkinlik Tasarımcısı

**InvokeMethod** Tasarımcısı bir etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.Activities.Statements.InvokeMethod> .

## <a name="the-invokemethod-activity"></a>InvokeMethod etkinliği

<xref:System.Activities.Statements.InvokeMethod>Belirtilen bir nesnenin veya türün ortak bir yöntemini çağırır.

### <a name="use-the-invokemethod-activity-designer"></a>InvokeMethod etkinlik tasarımcısını kullanma

**Araç kutusunun** **temel elemanlar** kategorisindeki **InvokeMethod** etkinlik tasarımcısına erişin. **InvokeMethod** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, içinde olduğu gibi, herhangi bir etkinliğin genellikle yerleştirildiği iş akışı Tasarımcısı yüzeyine bırakılabilir <xref:System.Activities.Statements.Sequence> . Etkinlik Tasarımcısı ' nın atılması, <xref:System.Activities.Statements.InvokeMethod> varsayılan bir InvokeMethod ile bir etkinlik oluşturur <xref:System.Activities.Activity.DisplayName%2A> . , <xref:System.Activities.Activity.DisplayName%2A> **InvokeMethod** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-invokemethod-properties"></a>InvokeMethod özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.InvokeMethod> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler özellik kılavuzunda düzenlenebilir ve bazıları İş Akışı Tasarımcısı yüzeyinde düzenlenebilirler.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin kolay adı <xref:System.Activities.Statements.InvokeMethod> . Varsayılan değer InvokeMethod ' dır.<br /><br /> Kesinlikle gerekli olmasa da, <xref:System.Activities.Activity.DisplayName%2A> en iyisi bir tane kullanmaktır.|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|Doğru|Etkinlik yürütüldüğünde çağrılacak yöntemin adı. Çağrılan yöntem **ortak** olarak bildirilmelidir. Bu özellik tasarımcı yüzeyinde düzenlenebilir ve zorunludur.|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|Yanlış|Çağrılan metodun parametre koleksiyonu. Parametrelerin, yöntem imzasında göründükleri sırada koleksiyona eklenmesi gerekir. Bu özelliği ayarlayabileceğiniz **Parametreler** iletişim kutusunu göstermek için, özellik kılavuzunun **Parametreler** alanındaki üç nokta düğmesine tıklayın. Parametreleri eklemek için **bağımsız değişken Oluştur** düğmesine tıklayın.|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|Yanlış|Yöntem çağrısının dönüş değeri.|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|Doğru|Metodun zaman uyumsuz olarak verilip verilmeyeceğini belirtir. Varsayılan değer **false** 'dur.|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|Yanlış|Çağrılacak yöntemi içeren nesne. Bu özellik, tasarımcı yüzeyinde düzenlenebilir.<br /><br /> Ya da ' <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> nin ayarlanması gerekiyor.|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|Yanlış|Türü <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> . Bu özellik tasarımcı yüzeyinde düzenlenebilir. Bu özellik yalnızca çağrılan yöntem static ise ayarlanmalıdır.|

Parametreleri bir C# **Out** parametresi olarak geçirmek için (örneğin, `Method1(out myParam))` **InOutArgument** yerine **OutArgument** kullanın)

**TargetObject** veya **Result** adlı bağımsız değişkenlerle Yöntemler etkinlik kullanılarak çağrılamaz <xref:System.Activities.Statements.InvokeMethod> . Bunun nedeni, etkinliğin öğesine ve ' a <xref:System.Activities.Statements.InvokeMethod> kaydolmasının nedenidir <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> <xref:System.Activities.Statements.InvokeMethod.Result%2A> <xref:System.Activities.Activity.CacheMetadata%2A> .

İçindeki parametreleri kaydetme algoritması <xref:System.Activities.Activity.CacheMetadata%2A> Aşağıdaki listede gösterilmiştir:

1. Yazmaç <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> bağımsız değişkeni.

2. Yazmaç <xref:System.Activities.Statements.InvokeMethod.Result%2A> bağımsız değişkeni.

3. <xref:System.Activities.Statements.InvokeMethod.Parameters%2A>Koleksiyonda yineleyin ve her bağımsız değişkeni kaydedin.

Elde edilen özel durum <xref:System.Activities.InvalidWorkflowException> Şu iletiyi taşıyan türde: ' InvokeMethod ': ' TargetObject ' adlı bir değişken, RuntimeArgument veya DelegateArgument zaten var. Adlar bir ortam kapsamı içinde benzersiz olmalıdır.

Bu kısıtlama ve için geçerlidir <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A> . İş akışı bağımsız değişkenleri değildir ve bu nedenle <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> yöntemdeki etkinliğin koleksiyonunda kayıtlı değildir <xref:System.Activities.Statements.InvokeMethod> <xref:System.Activities.Activity.CacheMetadata%2A> .

## <a name="see-also"></a>Ayrıca bkz.

- [Temel Türler](../workflow-designer/primitives-activity-designers.md)
- [Ata](../workflow-designer/assign-activity-designer.md)
- [Gecikme](../workflow-designer/delay-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)
