---
title: İş Akışı Tasarımcısı - InvokeMethod Etkinlik Tasarımcısı
description: InvokeMethod etkinliği hakkında bilgi edinmek ve InvokeMethod etkinlik tasarımcısını kullanarak InvokeMethod etkinliği oluşturma ve yapılandırma hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: fa26f068b723c4c67c09017eab5a5a5e7ca210fd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122114712"
---
# <a name="invokemethod-activity-designer"></a>InvokeMethod Etkinlik Tasarımcısı

**InvokeMethod** tasarımcısı bir etkinlik oluşturmak ve yapılandırmak için <xref:System.Activities.Statements.InvokeMethod> kullanılır.

## <a name="the-invokemethod-activity"></a>InvokeMethod etkinliği

belirtilen <xref:System.Activities.Statements.InvokeMethod> bir nesnenin veya türün genel yöntemini çağıran.

### <a name="use-the-invokemethod-activity-designer"></a>InvokeMethod Etkinlik Tasarımcısını Kullanma

Araç Kutusunun Temel Öğeler kategorisindeki **InvokeMethod** **etkinlik** tasarımcısına **erişin.** **InvokeMethod** etkinlik tasarımcısı **Araç** Kutusundan sürüklenerek İş Akışı Tasarımcısı yüzeyine bırakılır ve genellikle içinde olduğu gibi herhangi bir etkinliğin yerleştirilmelerini <xref:System.Activities.Statements.Sequence> sağlar. Etkinlik tasarımcısını bırakarak varsayılan <xref:System.Activities.Statements.InvokeMethod> <xref:System.Activities.Activity.DisplayName%2A> InvokeMethod değerine sahip bir etkinlik oluşturur. <xref:System.Activities.Activity.DisplayName%2A>, **InvokeMethod** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzundaki **DisplayName** kutusunda düzenlenebilir.

### <a name="the-invokemethod-properties"></a>InvokeMethod özellikleri

Aşağıdaki tabloda özellikler <xref:System.Activities.Statements.InvokeMethod> ve bunların tasarımcıda nasıl kullanıldıkları açık bulunmaktadır. Bu özellikler özellik kılavuzunda düzenlenebilir ve bazıları da İş Akışı Tasarımcısı düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin kolay <xref:System.Activities.Statements.InvokeMethod> adı. Varsayılan değer InvokeMethod'tır.<br /><br /> kesinlikle <xref:System.Activities.Activity.DisplayName%2A> gerekli değildir, ancak en iyisi bir tane kullanmaktır.|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|Doğru|Etkinlik yürütülürken çağrılecek yöntemin adı. Çağrınan yöntem genel olarak bildir **gerekir.** Bu özellik tasarımcı yüzeyinde düzenlenebilir ve zorunludur.|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|Yanlış|Çağrılı yöntemin parametre koleksiyonu. Parametrelerin koleksiyona, yöntem imzasıyla aynı sırada ekleniyor olması gerekir. Bu özelliği **ayarlayabilirsiniz** Parametreler iletişim kutusunu görüntülemek için özellik kılavuzunda Parametreler **alanında** üç nokta düğmesine tıklayın. Parametreleri **eklemek için** Bağımsız Değişken Oluştur düğmesine tıklayın.|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|Yanlış|Yöntem çağrısının dönüş değeri.|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|Doğru|Yöntemin zaman uyumsuz olarak çağrılıp çağrıl olmadığını belirtir. Varsayılan değer **False'tır.**|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|Yanlış|Çağrı yapılacak yöntemi içeren nesne. Bu özellik tasarımcı yüzeyinde düzenlenebilir.<br /><br /> veya <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> 'nin ayarlanmış olması gerekir.|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|Yanlış|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>türü. Bu özellik tasarımcı yüzeyinde düzenlenebilir. Bu özellik yalnızca adlı yöntem statikse ayar olmalıdır.|

Parametreleri bir **C#** out parametresi olarak (örneğin, `Method1(out myParam))` ), **InOutArgument** yerine **OutArgument** kullanarak

**TargetObject** veya **Result** adlı bağımsız değişkenlere sahip yöntemler etkinlik kullanılarak <xref:System.Activities.Statements.InvokeMethod> çağrılamayacak. Bunun nedeni etkinliğin <xref:System.Activities.Statements.InvokeMethod> , ve girişlerini <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> <xref:System.Activities.Statements.InvokeMethod.Result%2A> kaydetmesidir. <xref:System.Activities.Activity.CacheMetadata%2A>

'de parametreleri kaydetme algoritması <xref:System.Activities.Activity.CacheMetadata%2A> aşağıdaki listede gösterilmiştir:

1. Register <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> bağımsız değişkeni.

2. Register <xref:System.Activities.Statements.InvokeMethod.Result%2A> bağımsız değişkeni.

3. Koleksiyonda iterate <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> ve her bağımsız değişkeni kaydetme.

Sonuçta elde edilen özel durum şu iletiyle <xref:System.Activities.InvalidWorkflowException> türündedir: 'InvokeMethod': 'TargetObject' adıyla bir değişken, RuntimeArgument veya DelegateArgument zaten var. Adlar bir ortam kapsamında benzersiz olmalıdır.

Bu kısıtlama ve için geçerli <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A> değildir. Bunlar iş akışı bağımsız değişkenleri değildir ve bu nedenle yönteminde <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> etkinliğin <xref:System.Activities.Statements.InvokeMethod> koleksiyonuna kayıtlı <xref:System.Activities.Activity.CacheMetadata%2A> değildir.

## <a name="see-also"></a>Ayrıca bkz.

- [Temel Türler](../workflow-designer/primitives-activity-designers.md)
- [Atamak](../workflow-designer/assign-activity-designer.md)
- [Gecikme](../workflow-designer/delay-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)
