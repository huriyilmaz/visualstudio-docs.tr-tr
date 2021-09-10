---
title: İş Akışı Tasarımcısı - Etkinlik Tasarımcısı Atama
description: Bir Ata etkinliği oluşturmak ve yapılandırmak için Etkinlik ata tasarımcısını nasıl kullanabileceğiniz ve Ata etkinliğinin bir değişkene veya bağımsız değişkene nasıl değer atadığınız hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 524d55608b8cc75deea1c876ab03a4a437ad2049
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963711"
---
# <a name="assign-activity-designer"></a>Assign Etkinlik Tasarımcısı

Etkinlik **ata** tasarımcısı, etkinlik oluşturmak ve yapılandırmak için <xref:System.Activities.Statements.Assign> kullanılır.

## <a name="the-assign-activity"></a>Etkinlik Atama

Etkinlik <xref:System.Activities.Statements.Assign> bir değişkene veya bağımsız değişkene bir değer atar.

### <a name="using-the-assign-activity-designer"></a>Etkinlik Tasarımcısı Atamayı Kullanma

Etkinlik **ata** tasarımcısı, Araç  Kutusu sekmesine tıklayarak erişilen Araç Kutusu'nun Temel Öğeler kategorisinde  bulunabilir (Alternatif olarak, Görünüm menüsünden Araç Kutusu'nı veya CTRL+ALT+X'i seçin.)  

Etkinlik **ata** tasarımcısı Araç Kutusundan  sürüklenip herhangi bir etkinliğin yerleştirilme İş Akışı Tasarımcısı bir içinde olduğu bir yere <xref:System.Activities.Statements.Sequence> bırakılır. Etkinlik **tasarımcısını ata** bırakarak varsayılan <xref:System.Activities.Statements.Assign> **DisplayName** değeri Ata olan bir etkinlik oluşturur. <xref:System.Activities.Activity.DisplayName%2A>, Assign etkinlik tasarımcısının üst  bilgisinde veya özellik kılavuzundaki **DisplayName** kutusunda düzenlenebilir.

### <a name="the-assign-properties"></a>Özellikleri Ata

Aşağıdaki tablo, <xref:System.Activities.Statements.Assign> özellikleri gösterir ve tasarımcıda nasıl kullanıldıklarını açıklar. Bu özellikler özellik kılavuzunda düzenlenebilir ve bazı özellikler yüzeyde İş Akışı Tasarımcısı düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin kolay <xref:System.Activities.Statements.Assign> adı. Varsayılan değer Ata'dır. Değer <xref:System.Activities.Activity.DisplayName%2A> kesinlikle gerekli değildir ancak bir değer kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.Assign.To%2A>|Doğru|değişkeninin atandığı değişken <xref:System.Activities.Statements.Assign.Value%2A> veya bağımsız değişken. Değer, geçerli bir Visual Basic olmalıdır. Özelliğini ayarlamak için, Etkinlik Visual Basic veya özellik **kılavuzunda**  Yer Alan kutusuna bir Visual Basic ifadesi yazın.|
|<xref:System.Activities.Statements.Assign.Value%2A>|Doğru|Değişkenine atanan değer. değerini ayarlamak için, Visual Basic tasarımcısında veya özellik kılavuzunda Değer kutusuna bir Visual Basic <xref:System.Activities.Statements.Assign.Value%2A> ifadesi yazın.  |

## <a name="see-also"></a>Ayrıca bkz.

- [Temel Türler](../workflow-designer/primitives-activity-designers.md)
- [Gecikme](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)