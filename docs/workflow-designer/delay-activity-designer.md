---
title: İş Akışı Tasarımcısı - Delay Etkinlik Tasarımcısı
description: Gecikme etkinlikleri ve Gecikme etkinliği oluşturmak ve yapılandırmak için Gecikme etkinliği tasarımcısını nasıl kullanabileceğiniz hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 2d59f0db70804049a0392350942000d4331715021fb30f7ab43183d7326d02f4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121440545"
---
# <a name="delay-activity-designer"></a>Delay Etkinlik Tasarımcısı

Etkinlik **oluşturmak** ve yapılandırmak için Delay etkinlik tasarımcısı <xref:System.Activities.Statements.Delay> kullanılır.

## <a name="the-delay-activity"></a>Gecikme etkinliği

Etkinlik, <xref:System.Activities.Statements.Delay> iş akışının yürütülmesini belirli bir süre geciktirmektedir.

### <a name="use-the-delay-activity-designer"></a>Delay Etkinlik Tasarımcısını Kullanma

Gecikme **etkinliği** tasarımcısı, araç  kutusunun Araç Kutusu sekmesine tıklayarak erişilen Araç Kutusunun **Temel** öğeler kategorisinde İş Akışı Tasarımcısı. Alternatif olarak Görünüm **menüsünden Araç** Kutusu'nı **seçin** veya **Ctrl** Alt X + **tuşlarına** + **basın.**

Gecikme **etkinliği** tasarımcısı Araç Kutusundan **sürüklenip** bir içinde olduğu gibi İş Akışı Tasarımcısı yerleştirildikten sonra bu alan yüzeyine <xref:System.Activities.Statements.Sequence> bırakılır. Etkinlik tasarımcısını bırakarak, varsayılan <xref:System.Activities.Statements.Delay> Delay değerine sahip bir <xref:System.Activities.Activity.DisplayName%2A> etkinlik oluşturur. <xref:System.Activities.Activity.DisplayName%2A>, Delay etkinlik tasarımcısının üst  bilgisinde veya özellik kılavuzundaki **DisplayName** kutusunda düzenlenebilir.

### <a name="the-delay-properties"></a>Gecikme özellikleri

Aşağıdaki tabloda özellikler <xref:System.Activities.Statements.Delay> ve bunların tasarımcıda nasıl kullanıldıkları açık bulunmaktadır. Bu özellikler özellik kılavuzunda düzenlenebilir ve bunlardan bazıları, İş Akışı Tasarımcısı düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin kolay <xref:System.Activities.Statements.Delay> adı. Varsayılan değer Gecikme'dir. Değer kesinlikle gerekli değildir ancak en iyi yöntem bunlardan birini <xref:System.Activities.Activity.DisplayName%2A> kullanmaktır.|
|<xref:System.Activities.Statements.Delay.Duration%2A>|Doğru|İş akışını geciktirme süresi. Bu özellik, özellik kılavuzunda ayarlanır. Süre miktarını belirtmek için <xref:System.TimeSpan> 00:00:00 biçiminde bir değişmez Visual Basic bir ifade yazın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Temel Türler](../workflow-designer/primitives-activity-designers.md)
- [Atamak](../workflow-designer/assign-activity-designer.md)
- [Delay Etkinlik Tasarımcısı](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)