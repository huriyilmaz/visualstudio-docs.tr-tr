---
title: İş Akışı Tasarımcısı-InvokeDelegate
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 5227d96e3fad03dd3e3309523a6d2c68a1abdc11
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650187"
---
# <a name="invokedelegate"></a>InvokeDelegate

**InvokeDelegate** Tasarımcısı, bir <xref:System.Activities.Statements.InvokeDelegate> etkinliği oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-invokedelegate-activity"></a>InvokeDelegate etkinliği

@No__t_0 ortak bir temsilciyi çağırır.

### <a name="use-the-invokedelegate-activity-designer"></a>InvokeDelegate etkinlik tasarımcısını kullanma

**Araç kutusunun** **temel elemanlar** kategorisindeki **InvokeDelegate** etkinlik tasarımcısına erişin. **InvokeDelegate** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, bir <xref:System.Activities.Statements.Sequence> içinde olduğu gibi, her zaman etkinliklerin genellikle yerleştirildiği iş akışı Tasarımcısı yüzeyine bırakılabilir. Etkinlik tasarımcısının atılması, InvokeDelegate 'in varsayılan <xref:System.Activities.Activity.DisplayName%2A> bir <xref:System.Activities.Statements.InvokeDelegate> etkinlik oluşturur. @No__t_0, **InvokeDelegate** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-invokedelegate-properties"></a>InvokeDelegate özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.InvokeDelegate> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler özellik kılavuzunda düzenlenebilir ve bazıları İş Akışı Tasarımcısı yüzeyinde düzenlenebilirler.

|Özellik adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|@No__t_0 etkinliğinin kolay adı. Varsayılan değer InvokeDelegate ' dir.<br /><br /> @No__t_0 kesinlikle gerekli olmasa da, en iyisi bir tane kullanmaktır.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|Doğru|Etkinlik yürütüldüğünde çağrılacak <xref:System.Activities.ActivityDelegate> adı. Bu özellik tasarımcı yüzeyinde düzenlenebilir ve zorunludur.|
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|Çağrılan temsilcinin bağımsız değişken koleksiyonu. Anahtarlar <xref:System.Activities.ActivityDelegate> parametre nesnelerinin adlarıdır ve değerler, ifadeleri değerlendirilen ve karşılık gelen parametre nesnelerine atanan bağımsız değişkenlerdir. Bu özelliği ayarlayabileceğiniz **DelegateArguments** iletişim kutusunu göstermek için, özellik kılavuzunun **DelegateArguments** alanındaki üç nokta düğmesine tıklayın. Bağımsız değişkenleri eklemek için **bağımsız değişken Oluştur** alanına tıklayın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: İş Akışı Tasarımcısında etkinlik temsilcileri tanımlama ve kullanma](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)