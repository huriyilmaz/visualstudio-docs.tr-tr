---
title: İş Akışı Tasarımcısı-throw etkinlik Tasarımcısı
description: Throw etkinliği ve throw etkinliği oluşturmak ve yapılandırmak için throw etkinliği tasarımcısını nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a1ffd0a9dda243e53431e419910b866853cd3932
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969106"
---
# <a name="throw-activity-designer"></a>Throw Etkinlik Tasarımcısı

**Throw** etkinlik Tasarımcısı, etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.Activities.Statements.Throw> .

## <a name="the-throw-activity"></a>Throw etkinliği

<xref:System.Activities.Statements.Throw>Etkinlik bir özel durum oluşturur.

### <a name="using-the-throw-activity-designer"></a>Throw etkinlik tasarımcısını kullanma

**Araç kutusunun** **hata işleme** kategorisindeki **throw** etkinlik tasarımcısına erişin.

**Throw** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, içindeki gibi etkinliklerin genellikle yerleştirildiği iş akışı Tasarımcısı yüzeyine bırakılabilir <xref:System.Activities.Statements.Sequence> . Bu <xref:System.Activities.Statements.Throw> , throw öğesinin varsayılan **DisplayName** ile bir etkinlik oluşturur. <xref:System.Activities.Activity.DisplayName%2A>Değer, **throw** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir. Özellik, özellik <xref:System.Activities.Statements.Throw.Exception%2A> kılavuzunda düzenlenmelidir.

### <a name="the-throw-properties"></a>Throw özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.Throw> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin isteğe bağlı kolay adını belirtir <xref:System.Activities.Statements.Throw> . Varsayılan değer throw ' dir.|
|<xref:System.Activities.Statements.Throw.Exception%2A>|Doğru|Throw özel durumu. Bu özel durumun türevi olması gerekir <xref:System.Exception> . Özel durumu belirtmek için, özellik kılavuzuna bir Visual Basic ifadesi yazın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyon](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Throw Etkinlik Tasarımcısı](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)
