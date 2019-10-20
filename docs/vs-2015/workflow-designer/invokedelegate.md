---
title: InvokeDelegate | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
caps.latest.revision: 3
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc35aec714255b467431488936605fb37009db9d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659011"
---
# <a name="invokedelegate"></a>InvokeDelegate

**InvokeDelegate** Tasarımcısı, bir <xref:System.Activities.Statements.InvokeDelegate> etkinliği oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-invokedelegate-activity"></a>InvokeDelegate etkinliği

@No__t_0 ortak bir temsilciyi çağırır.

### <a name="using-the-invokedelegate-activity-designer"></a>InvokeDelegate etkinlik tasarımcısını kullanma

**InvokeDelegate** etkinlik Tasarımcısı, **araç kutusu [!INCLUDE[wfd2](../includes/wfd2-md.md)]** **sekmesine (alternatif olarak,** **Görünüm** menüsünden **araç çubuğu** ' nu seçin veya CRTL + ALT + X.)

**InvokeDelegate** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, bir <xref:System.Activities.Statements.Sequence> içinde olduğu gibi, her zaman etkinliklerin genellikle yerleştirildiği [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyine bırakılabilir. Bu, InvokeDelegate 'in varsayılan <xref:System.Activities.Activity.DisplayName%2A> bir <xref:System.Activities.Statements.InvokeDelegate> etkinliği oluşturur. @No__t_0, **InvokeDelegate** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-invokedelegate-properties"></a>InvokeDelegate özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.InvokeDelegate> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler özellik kılavuzunda düzenlenebilir ve bazıları [!INCLUDE[wfd2](../includes/wfd2-md.md)]designer yüzeyinde düzenlenebilirler.

|Özellik adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|@No__t_0 etkinliğinin kolay adı. Varsayılan değer InvokeDelegate ' dir.<br /><br /> @No__t_0 kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|Doğru|Etkinlik yürütüldüğünde çağrılacak <xref:System.Activities.ActivityDelegate> adı. Bu özellik, tasarımcı yüzeyinde düzenlenebilir. Bu zorunlu bir özelliktir.|
|<<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|Çağrılan temsilcinin bağımsız değişken koleksiyonu. Anahtarlar, <xref:System.Activities.ActivityDelegate> <xref:System.Activities.DelegateArgument> nesnelerinin adlarıdır ve değerler, ifadeleri değerlendirilen ve karşılık gelen <xref:System.Activities.DelegateArgument> nesnelerine atanan bağımsız değişkenlerdir. Özellik kılavuzunda, **DelegateArguments** alanındaki üç nokta düğmesine tıklayın, bu özelliği ayarlamanıza olanak sağlamak Için **DelegateArguments** iletişim kutusu görüntülenir. Bağımsız değişkenleri eklemek için **bağımsız değişken Oluştur** alanına tıklayın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: İş Akışı Tasarımcısında etkinlik temsilcileri tanımlama ve kullanma](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)