---
title: İş Akışı Tasarımcısı - Rethrow Etkinlik Tasarımcısı
description: Rethrow etkinliğini ve Rethrow etkinlik tasarımcısını kullanarak bir Rethrow etkinliği oluşturma ve yapılandırma hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 5508555d2e4347a96e1eaf7319270cf3f95f3177
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963763"
---
# <a name="rethrow-activity-designer"></a>Rethrow Etkinlik Tasarımcısı

**Rethrow etkinlik** tasarımcısı bir etkinlik oluşturmak ve yapılandırmak için <xref:System.Activities.Statements.Rethrow> kullanılır.

## <a name="the-rethrow-activity"></a>Rethrow etkinliği

Etkinlik <xref:System.Activities.Statements.Rethrow> daha önce bir özel durum oluşturur. Bu etkinlik yalnızca etkinlikte bir <xref:System.Activities.Statements.Catch> işleyicide <xref:System.Activities.Statements.TryCatch> kullanılabilir.

### <a name="use-the-rethrow-activity-designer"></a>ReThrow Etkinlik Tasarımcısını Kullanma

Araç Kutusunun Hata İşleme kategorisindeki **Rethrow** etkinlik  **tasarımcısına erişin.** **Rethrow etkinlik** tasarımcısı Araç Kutusundan  sürüklenip bir içinde olduğu gibi İş Akışı Tasarımcısı yerleştirilmelerinden sonra araç yüzeyine <xref:System.Activities.Statements.Sequence> bırakılır. Etkinlik tasarımcısı bırakarak, varsayılan <xref:System.Activities.Statements.Rethrow> **Throw DisplayName değerine sahip bir** etkinlik oluşturur. Değer Rethrow etkinlik tasarımcısının üst bilgisinde veya <xref:System.Activities.Activity.DisplayName%2A> özellik kılavuzundaki **DisplayName** kutusunda düzenlenebilir. 

### <a name="the-rethrow-properties"></a>Rethrow özellikleri

Aşağıdaki tabloda özellikler <xref:System.Activities.Statements.Rethrow> ve tasarımcıda nasıl kullanıldıkları açık bulunmaktadır:

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin isteğe bağlı kolay adını <xref:System.Activities.Statements.Rethrow> belirtir. Varsayılan değer Rethrow'dır.|

## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyon](../workflow-designer/collection-activity-designers.md)
- [Atmak](../workflow-designer/throw-activity-designer.md)
- [Trycatch](../workflow-designer/trycatch-activity-designer.md)
