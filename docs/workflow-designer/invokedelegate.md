---
title: İş Akışı Tasarımcısı - InvokeDelegate
description: InvokeDelegate tasarımcısı ve InvokeDelegate tasarımcısını kullanarak invokeDelegate etkinliği oluşturma ve yapılandırma hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 12fd42bd51a252470c2b7d4fbae23581847ddf0f6d3dede60f6e2659215d80fd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121393516"
---
# <a name="invokedelegate"></a>InvokeDelegate

**InvokeDelegate** tasarımcısı bir etkinlik oluşturmak ve yapılandırmak için <xref:System.Activities.Statements.InvokeDelegate> kullanılır.

## <a name="the-invokedelegate-activity"></a>InvokeDelegate etkinliği

, <xref:System.Activities.Statements.InvokeDelegate> bir genel temsilciyi çağırıyor.

### <a name="use-the-invokedelegate-activity-designer"></a>InvokeDelegate Etkinlik Tasarımcısını Kullanma

Araç Kutusunun Temel Öğeler kategorisindeki **InvokeDelegate** **etkinlik** **tasarımcısına erişin.** **InvokeDelegate** etkinlik tasarımcısı **Araç** Kutusundan sürüklenerek İş Akışı Tasarımcısı yüzeyine bırakılır ve genellikle bir içinde olduğu gibi herhangi bir etkinliğin yerleştirilmelerini <xref:System.Activities.Statements.Sequence> sağlar. Etkinlik tasarımcısını bırakarak, <xref:System.Activities.Statements.InvokeDelegate> <xref:System.Activities.Activity.DisplayName%2A> invokeDelegate varsayılan değerine sahip bir etkinlik oluşturur. <xref:System.Activities.Activity.DisplayName%2A>, **InvokeDelegate** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzundaki **DisplayName** kutusunda düzenlenebilir.

### <a name="the-invokedelegate-properties"></a>InvokeDelegate özellikleri

Aşağıdaki tablo, <xref:System.Activities.Statements.InvokeDelegate> özellikleri gösterir ve tasarımcıda nasıl kullanıldıklarını açıklar. Bu özellikler özellik kılavuzunda düzenlenebilir ve bazıları da İş Akışı Tasarımcısı düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin kolay <xref:System.Activities.Statements.InvokeDelegate> adı. Varsayılan değer InvokeDelegate'tir.<br /><br /> kesinlikle <xref:System.Activities.Activity.DisplayName%2A> gerekli değildir, ancak en iyisi bir tane kullanmaktır.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|Doğru|Etkinlik <xref:System.Activities.ActivityDelegate> yürütülürken çağrılecek olan adı. Bu özellik tasarımcı yüzeyinde düzenlenebilir ve zorunludur.|
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|Yanlış|Çağrılı temsilcinin bağımsız değişken koleksiyonu. Anahtarlar, üzerinde parametre nesnelerinin adlarıdır ve değerler, ifadeleri değerlendirilip karşılık gelen parametre nesnelerine atanan <xref:System.Activities.ActivityDelegate> bağımsız değişkenlerdir. Bu özelliği **ayarlayabilirsiniz DelegateArguments** iletişim kutusunu görüntülemek için özellik kılavuzunda **DelegateArguments** alanında üç nokta düğmesine tıklayın. Bağımsız değişkenleri **eklemek için** Bağımsız Değişken Oluştur alanına tıklayın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: İş Akışı Tasarımcısında etkinlik temsilcileri tanımlama ve kullanma](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)