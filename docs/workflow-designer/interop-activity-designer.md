---
title: İş Akışı Tasarımcısı - Birlikte Çalışma Etkinliği Tasarımcısı
description: Birlikte çalışma etkinliği tasarımcısı hakkında bilgi ve birlikte çalışma etkinliği oluşturmak ve yapılandırmak için Birlikte Çalışma etkinlik tasarımcısını nasıl kullanabileceğiniz hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
author: jillre
ms.author: jillfra
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 785fa491d78c0286404918f01149752af2f0dc69
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963754"
---
# <a name="interop-activity-designer"></a>Interop Etkinlik Tasarımcısı

Birlikte **çalışma** etkinliği tasarımcısı bir etkinlik oluşturmak ve yapılandırmak için <xref:System.Activities.Statements.Interop> kullanılır.

## <a name="the-interop-activity"></a>Birlikte Çalışma Etkinliği

Etkinlik, <xref:System.Activities.Statements.Interop> bir iş akışından türeyen türlerin <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> yürütülmesini yönetir.

### <a name="use-the-interop-activity-designer"></a>Birlikte Çalışma Etkinliği Tasarımcısını Kullanma

Birlikte **çalışma** etkinliği tasarımcısı, Araç Kutusu  **sekmesine** tıklayarak erişilen Araç Kutusunun Geçiş **kategorisinde** bulunabilir. Alternatif olarak Görünüm **menüsünden Araç** Kutusu'nı **seçin** veya **Ctrl** Alt X + **tuşlarına** + **basın.**

Etkinliği [içeren](../workflow-designer/migration-activity-designers.md) Geçiş kategorisi yalnızca projeniz 4 (tam) veya sonraki bir <xref:System.Activities.Statements.Interop> .NET Framework hedefleniyorsa Araç  Kutusunda görünür. Gerekirse, projenizin hedefle olduğu çerçeve sürümünü değiştirebilirsiniz.

Birlikte **çalışma** etkinliği tasarımcısı Araç Kutusundan **sürüklenip** bir içinde olduğu gibi İş Akışı Tasarımcısı yerleştirildikten sonra araç yüzeyine <xref:System.Activities.Statements.Sequence> bırakılır. Birlikte Çalışma **etkinlik tasarımcısı** bırakarak varsayılan DisplayName of Interop <xref:System.Activities.Statements.Interop> ile **bir** etkinlik oluşturur. birlikte çalışma <xref:System.Activities.Activity.DisplayName%2A> etkinliği tasarımcısının üst **bilgisinde** veya özellik kılavuzundaki **DisplayName** kutusunda düzenleyebilirsiniz.

Birlikte çalışma **etkinliği tasarımcısında** veya özellik kılavuzunda  **ActivityType** kutusundaki metne göz atmak için tıklayın'a tıklayın ve Gözat ve **Bir .Net Türü Seç iletişim** kutusunu açın. Yalnızca iş akışı 3.0 veya iş akışı 3.5 etkinlikleri için türler gösterilir. Başka bir ifadeyle, yalnızca türetilen <xref:System.Workflow.ComponentModel.Activity> türler gösterilir. Bir tür belirtmek için bu kutuyu kullanma hakkında daha fazla bilgi için bkz. Gözat [ve Bir .NET Türü Seç İletişim Kutusu](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md).

### <a name="the-interop-properties"></a>Birlikte Çalışma Özellikleri

Aşağıdaki tablo, <xref:System.Activities.Statements.Interop> özellikleri gösterir ve tasarımcıda nasıl kullanıldıklarını açıklar. Bu özellikler özellik kılavuzunda veya İş Akışı Tasarımcısı düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin kolay <xref:System.Activities.Statements.Interop> adı. Varsayılan değer Birlikte **Çalışma'dır.** Görünen ad gerekli değildir, ancak bir ad sağlamak önerilir.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|Doğru|Etkinliğin içerdiği etkinliğin türünü <xref:System.Activities.Statements.Interop> belirtir. Belirtilen bu tür, türünden <xref:System.Workflow.ComponentModel.Activity> türetilmelidir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Geçiş](../workflow-designer/migration-activity-designers.md)