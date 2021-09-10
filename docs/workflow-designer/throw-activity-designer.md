---
title: İş Akışı Tasarımcısı - Throw Etkinlik Tasarımcısı
description: Throw etkinliği ve Throw etkinliği oluşturmak ve yapılandırmak için Throw etkinlik tasarımcısını nasıl kullanabileceğiniz hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 8517ac1cfc2a1a4ba0c3a1c28e17970bea6e1598
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963764"
---
# <a name="throw-activity-designer"></a>Throw Etkinlik Tasarımcısı

Throw **etkinlik** tasarımcısı, etkinlik oluşturmak ve yapılandırmak için <xref:System.Activities.Statements.Throw> kullanılır.

## <a name="the-throw-activity"></a>Throw Etkinliği

Etkinlik <xref:System.Activities.Statements.Throw> bir özel durum oluşturur.

### <a name="using-the-throw-activity-designer"></a>Throw Etkinlik Tasarımcısını Kullanma

Araç Kutusunun **Hata** İşleme kategorisinde **Throw etkinlik** tasarımcısına **erişin.**

**Throw** etkinlik tasarımcısı Araç Kutusundan **sürüklenip** bir içinde olduğu gibi İş Akışı Tasarımcısı yerleştirilmelerinden sonra araç yüzeyine <xref:System.Activities.Statements.Sequence> bırakılır. Bu, varsayılan <xref:System.Activities.Statements.Throw> Throw **DisplayName değerine sahip bir** etkinlik oluşturur. Değer <xref:System.Activities.Activity.DisplayName%2A> Throw etkinlik tasarımcısının üst  bilgisinde veya özellik kılavuzundaki **DisplayName** kutusunda düzenlenebilir. <xref:System.Activities.Statements.Throw.Exception%2A>özelliği, özellik kılavuzunda düzenlenemez.

### <a name="the-throw-properties"></a>Throw Özellikleri

Aşağıdaki tablo, <xref:System.Activities.Statements.Throw> özellikleri gösterir ve tasarımcıda nasıl kullanıldıklarını açıklar.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin isteğe bağlı kolay adını <xref:System.Activities.Statements.Throw> belirtir. Varsayılan değer Throw'tır.|
|<xref:System.Activities.Statements.Throw.Exception%2A>|Doğru|Atılan özel durum. Bu özel durum, 'den <xref:System.Exception> türetildi. Özel durumu belirtmek için özellik kılavuzuna Visual Basic bir ifade yazın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyon](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Throw Etkinlik Tasarımcısı](../workflow-designer/throw-activity-designer.md)
- [Trycatch](../workflow-designer/trycatch-activity-designer.md)
