---
title: InvokeMethod etkinlik Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fcfba979ba7fce4aeffab1fe9e9a5a3728e513af
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659001"
---
# <a name="invokemethod-activity-designer"></a>InvokeMethod Etkinlik Tasarımcısı
**InvokeMethod** Tasarımcısı bir etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.Activities.Statements.InvokeMethod> .

## <a name="the-invokemethod-activity"></a>InvokeMethod etkinliği
 <xref:System.Activities.Statements.InvokeMethod>Belirtilen bir nesnenin veya türün ortak bir yöntemini çağırır.

### <a name="using-the-invokemethod-activity-designer"></a>InvokeMethod etkinlik tasarımcısını kullanma
 **InvokeMethod** etkinlik **Tasarımcısı araç kutusu sekmesine** tıklanarak erişilen **Primitives** (alternatif olarak, **Toolbox** [!INCLUDE[wfd2](../includes/wfd2-md.md)] **Görünüm** menüsünden **araç çubuğu** ' nu veya Crtl + alt + X ' i seçerek) araç kutusu ' nda bulunan temel öğeler kategorisinde bulunabilir.

 **InvokeMethod** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, ancak [!INCLUDE[wfd2](../includes/wfd2-md.md)] içinde olduğu gibi, herhangi bir etkinliğin genellikle yerleştirildiği yüzeyine bırakılabilir <xref:System.Activities.Statements.Sequence> . Bu <xref:System.Activities.Statements.InvokeMethod> , varsayılan bir InvokeMethod ile etkinlik oluşturur <xref:System.Activities.Activity.DisplayName%2A> . , <xref:System.Activities.Activity.DisplayName%2A> **InvokeMethod** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-invokemethod-properties"></a>InvokeMethod özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.InvokeMethod> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzunda düzenlenebilir ve bazıları [!INCLUDE[wfd2](../includes/wfd2-md.md)] Tasarımcı yüzeyinde düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin kolay adı <xref:System.Activities.Statements.InvokeMethod> . Varsayılan değer InvokeMethod ' dır.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>Kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|Doğru|Etkinlik yürütüldüğünde çağrılacak yöntemin adı. Çağrılan yöntem **ortak**olarak bildirilmelidir. Bu özellik, tasarımcı yüzeyinde düzenlenebilir. Bu zorunlu bir özelliktir.|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|Yanlış|Çağrılan metodun parametre koleksiyonu. Parametrelerin, yöntem imzasında göründükleri sırada koleksiyona eklenmesi gerekir. Özellik kılavuzunda **Parametreler** alanındaki üç nokta düğmesine tıklayın, bu özelliği ayarlamanıza olanak sağlamak için **Parametreler** iletişim kutusu görüntülenir. Parametreleri eklemek için **bağımsız değişken Oluştur** düğmesine tıklayın.|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|Yanlış|Yöntem çağrısının dönüş değeri.|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|Doğru|Metodun zaman uyumsuz olarak verilip verilmeyeceğini belirtir. Varsayılan değer **false**'dur.|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|Yanlış|Çağrılacak yöntemi içeren nesne. Bu özellik, tasarımcı yüzeyinde düzenlenebilir.<br /><br /> Ya da ' <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> nin ayarlanması gerekiyor.|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|Yanlış|Türü <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> . Bu özellik tasarımcı yüzeyinde düzenlenebilir. Bu özellik yalnızca çağrılan yöntem static ise ayarlanmalıdır.|

 Parametreleri bir C# **Out** parametresi olarak geçirmek için (örneğin, `Method1(out myParam)),` **InOutArgument** yerine **OutArgument** kullanmanız gerekir

 **TargetObject** veya **Result** adlı bağımsız değişkenlerle Yöntemler etkinlik kullanılarak çağrılamaz <xref:System.Activities.Statements.InvokeMethod> . Bunun nedeni, etkinliğin öğesine ve ' a <xref:System.Activities.Statements.InvokeMethod> kaydolmasının nedenidir <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> <xref:System.Activities.Statements.InvokeMethod.Result%2A> <xref:System.Activities.Activity.CacheMetadata%2A> .

 İçindeki parametreleri kaydetme algoritması <xref:System.Activities.Activity.CacheMetadata%2A> Aşağıdaki listede gösterilmiştir:

1. Yazmaç <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> bağımsız değişkeni.

2. Yazmaç <xref:System.Activities.Statements.InvokeMethod.Result%2A> bağımsız değişkeni.

3. <xref:System.Activities.Statements.InvokeMethod.Parameters%2A>Koleksiyonda yineleyin ve her bağımsız değişkeni kaydedin.

   Elde edilen özel durum <xref:System.Activities.InvalidWorkflowException> Şu iletiyi taşıyan türde: ' InvokeMethod ': ' TargetObject ' adlı bir değişken, RuntimeArgument veya DelegateArgument zaten var. Adlar bir ortam kapsamı içinde benzersiz olmalıdır.

   Bu kısıtlama, <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A> iş akışı bağımsız değişkenleri olmadığından ve bu nedenle <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> <xref:System.Activities.Statements.InvokeMethod> yöntemdeki etkinlik koleksiyonunda kayıtlı <xref:System.Activities.Activity.CacheMetadata%2A> olmadığından, için geçerlidir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Temel elemanlar](../workflow-designer/primitives-activity-designers.md) [atama](../workflow-designer/assign-activity-designer.md) [süresi](../workflow-designer/delay-activity-designer.md) [WriteLine](../workflow-designer/writeline-activity-designer.md)