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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659011"
---
# <a name="invokedelegate"></a>InvokeDelegate

**InvokeDelegate** Tasarımcısı, etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.Activities.Statements.InvokeDelegate> .

## <a name="the-invokedelegate-activity"></a>InvokeDelegate etkinliği

<xref:System.Activities.Statements.InvokeDelegate>Ortak bir temsilciyi çağırır.

### <a name="using-the-invokedelegate-activity-designer"></a>InvokeDelegate etkinlik tasarımcısını kullanma

**InvokeDelegate** etkinlik **Tasarımcısı araç kutusu sekmesine** tıklanarak erişilen **Primitives** (alternatif olarak, **Toolbox** [!INCLUDE[wfd2](../includes/wfd2-md.md)] **Görünüm** menüsünden **araç çubuğu** ' nu veya Crtl + alt + X ' i seçerek) araç kutusu ' nda bulunan temel öğeler kategorisinde bulunabilir.

**InvokeDelegate** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, [!INCLUDE[wfd2](../includes/wfd2-md.md)] içinde olduğu gibi, herhangi bir etkinliğin genellikle yerleştirildiği yüzeyine bırakılabilir <xref:System.Activities.Statements.Sequence> . Bu <xref:System.Activities.Statements.InvokeDelegate> , varsayılan bir InvokeDelegate ile bir etkinlik oluşturur <xref:System.Activities.Activity.DisplayName%2A> . , <xref:System.Activities.Activity.DisplayName%2A> **InvokeDelegate** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-invokedelegate-properties"></a>InvokeDelegate özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.InvokeDelegate> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzunda düzenlenebilir ve bazıları [!INCLUDE[wfd2](../includes/wfd2-md.md)] Tasarımcı yüzeyinde düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin kolay adı <xref:System.Activities.Statements.InvokeDelegate> . Varsayılan değer InvokeDelegate ' dir.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>Kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|Doğru|<xref:System.Activities.ActivityDelegate>Etkinlik yürütüldüğünde çağrılacak öğesinin adı. Bu özellik, tasarımcı yüzeyinde düzenlenebilir. Bu zorunlu bir özelliktir.|
|<<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|Yanlış|Çağrılan temsilcinin bağımsız değişken koleksiyonu. Anahtarlar içindeki <xref:System.Activities.DelegateArgument> nesnelerin adlarıdır <xref:System.Activities.ActivityDelegate> ve değerleri, ifadeleri değerlendirilen ve ilgili nesnelere atanan bağımsız değişkenlerdir <xref:System.Activities.DelegateArgument> . Özellik kılavuzunda, **DelegateArguments** alanındaki üç nokta düğmesine tıklayın, bu özelliği ayarlamanıza olanak sağlamak Için **DelegateArguments** iletişim kutusu görüntülenir. Bağımsız değişkenleri eklemek için **bağımsız değişken Oluştur** alanına tıklayın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: İş Akışı Tasarımcısında etkinlik temsilcileri tanımlama ve kullanma](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)