---
title: İş Akışı Tasarımcısı-Rethrow etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3cb73a674e702d54f970c5dea7ec051f100382c9
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114757"
---
# <a name="rethrow-activity-designer"></a>Rethrow Etkinlik Tasarımcısı

**Rethrow** etkinlik Tasarımcısı <xref:System.Activities.Statements.Rethrow> etkinlik oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-rethrow-activity"></a>Rethrow etkinliği

<xref:System.Activities.Statements.Rethrow> etkinliği daha önce oluşturulan bir özel durum oluşturur. Bu etkinlik, <xref:System.Activities.Statements.TryCatch> etkinliğinde yalnızca bir <xref:System.Activities.Statements.Catch> işleyicisinde kullanılabilir.

### <a name="use-the-rethrow-activity-designer"></a>ReThrow etkinlik tasarımcısını kullanma

**Araç kutusunun** **hata Işleme** kategorisindeki **Rethrow** etkinlik tasarımcısına erişin. **Rethrow** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, her durumda (örneğin, <xref:System.Activities.Statements.Sequence>gibi) iş akışı Tasarımcısı yüzeyine bırakılabilir. Etkinlik Tasarımcısı ' nın atılması, varsayılan olarak throw **DisplayName** ile bir <xref:System.Activities.Statements.Rethrow> etkinliği oluşturur. <xref:System.Activities.Activity.DisplayName%2A> değeri **Rethrow** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-rethrow-properties"></a>Rethrow özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.Rethrow> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır:

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Rethrow> etkinliğinin isteğe bağlı kolay adını belirtir. Varsayılan değer Rethrow ' dir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyon](../workflow-designer/collection-activity-designers.md)
- [Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)
