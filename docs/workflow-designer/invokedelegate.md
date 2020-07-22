---
title: İş Akışı Tasarımcısı-InvokeDelegate
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
author: TerryGLee
ms.author: tglee
ms.workload:
- multiple
ms.openlocfilehash: 9e63fb7a766b79467749cc5181a575e0d35a07b8
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86876079"
---
# <a name="invokedelegate"></a>InvokeDelegate

**InvokeDelegate** Tasarımcısı, etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.Activities.Statements.InvokeDelegate> .

## <a name="the-invokedelegate-activity"></a>InvokeDelegate etkinliği

<xref:System.Activities.Statements.InvokeDelegate>Ortak bir temsilciyi çağırır.

### <a name="use-the-invokedelegate-activity-designer"></a>InvokeDelegate etkinlik tasarımcısını kullanma

**Araç kutusunun** **temel elemanlar** kategorisindeki **InvokeDelegate** etkinlik tasarımcısına erişin. **InvokeDelegate** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, içinde olduğu gibi, her zaman etkinliklerin genellikle yerleştirildiği iş akışı Tasarımcısı yüzeyine bırakılabilir <xref:System.Activities.Statements.Sequence> . Etkinlik Tasarımcısı ' nın atılması, <xref:System.Activities.Statements.InvokeDelegate> varsayılan bir InvokeDelegate ile bir etkinlik oluşturur <xref:System.Activities.Activity.DisplayName%2A> . , <xref:System.Activities.Activity.DisplayName%2A> **InvokeDelegate** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-invokedelegate-properties"></a>InvokeDelegate özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.InvokeDelegate> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler özellik kılavuzunda düzenlenebilir ve bazıları İş Akışı Tasarımcısı yüzeyinde düzenlenebilirler.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin kolay adı <xref:System.Activities.Statements.InvokeDelegate> . Varsayılan değer InvokeDelegate ' dir.<br /><br /> Kesinlikle gerekli olmasa da, <xref:System.Activities.Activity.DisplayName%2A> en iyisi bir tane kullanmaktır.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|Doğru|<xref:System.Activities.ActivityDelegate>Etkinlik yürütüldüğünde çağrılacak öğesinin adı. Bu özellik tasarımcı yüzeyinde düzenlenebilir ve zorunludur.|
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|Yanlış|Çağrılan temsilcinin bağımsız değişken koleksiyonu. Anahtarlar, içindeki parametre nesnelerinin adlarıdır <xref:System.Activities.ActivityDelegate> ve değerler, ifadeleri değerlendirilen ve ilgili parametre nesnelerine atanan bağımsız değişkenlerdir. Bu özelliği ayarlayabileceğiniz **DelegateArguments** iletişim kutusunu göstermek için, özellik kılavuzunun **DelegateArguments** alanındaki üç nokta düğmesine tıklayın. Bağımsız değişkenleri eklemek için **bağımsız değişken Oluştur** alanına tıklayın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: İş Akışı Tasarımcısında etkinlik temsilcileri tanımlama ve kullanma](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)