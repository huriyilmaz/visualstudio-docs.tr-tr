---
title: İş Akışı Tasarımcısı - Kalıcı Etkinlik Tasarımcısı
description: Kalıcı etkinlik hakkında bilgi ve Kalıcı etkinlik tasarımcısını kullanarak Bir Kalıcı etkinlik oluşturma ve yapılandırma hakkında bilgi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 2f0040b4c816ee55e6db7c59c3a74c53cedb51d5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633670"
---
# <a name="persist-activity-designer"></a>Persist Etkinlik Tasarımcısı

Etkinlik **oluşturmak** ve yapılandırmak için Kalıcı etkinlik tasarımcısı <xref:System.Activities.Statements.Persist> kullanılır.

## <a name="the-persist-activity"></a>Kalıcı Etkinlik

Etkinlik, <xref:System.Activities.Statements.Persist> mümkünse bir iş akışını diske kaydeder. Etkinlik, örneğin bir etkinlik içinde olduğu gibi <xref:System.Activities.Statements.Persist> kalıcılık olmayan bir bölgede <xref:System.Activities.Statements.TransactionScope> yürütülenemz. Kalıcılık olmayan <xref:System.Activities.Statements.Persist> bir kapsamda etkinlik kullanırsanız, çalışma zamanında bir özel durum oluşturur.

### <a name="using-the-persist-activity-designer"></a>Kalıcı Etkinlik Tasarımcısını Kullanma

Kalıcı **etkinlik** tasarımcısı, Araç Kutusu sekmesine tıklayarak erişilen Araç Kutusunun  Çalışma Zamanı kategorisinde bulunabilir (Alternatif  olarak, Görünüm menüsünden Araç Kutusu'nı veya CTRL+ALT+X'i seçin.)  

**Kalıcı etkinlik** tasarımcısı Araç Kutusundan  sürüklenip bir içinde olduğu gibi İş Akışı Tasarımcısı yerleştirildikten sonra araç yüzeyine <xref:System.Activities.Statements.Sequence> bırakılır. Bu, varsayılan <xref:System.Activities.Statements.Persist> **DisplayName** değeri Kalıcı olan bir etkinlik oluşturur. <xref:System.Activities.Activity.DisplayName%2A>, Kalıcı etkinlik tasarımcısının üst  bilgisinde veya özellik kılavuzundaki **DisplayName** kutusunda düzenlenebilir.

### <a name="the-persist-properties"></a>Kalıcı Özellikler

Aşağıdaki tablo, <xref:System.Activities.Statements.Persist> özellikleri gösterir ve tasarımcıda nasıl kullanıldıklarını açıklar. Bu özellikler özellik kılavuzunda düzenlenebilir ve bazı özellikler yüzeyde İş Akışı Tasarımcısı düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin kolay <xref:System.Activities.Statements.Persist> adı. Varsayılan değer Kalıcı'dır. Görünen ad kesinlikle gerekli değildir ancak görünen ad kullanmak en iyi uygulamadır.|

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı](../workflow-designer/runtime-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
