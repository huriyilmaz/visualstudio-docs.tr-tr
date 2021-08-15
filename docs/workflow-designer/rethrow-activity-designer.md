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
ms.openlocfilehash: d758f754a7c8e57b913bd7f1211cc70355f62ca20b93c973cbd3709a60684b00
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121243360"
---
# <a name="rethrow-activity-designer"></a>Rethrow Etkinlik Tasarımcısı

**Rethrow etkinlik** tasarımcısı bir etkinlik oluşturmak ve yapılandırmak için <xref:System.Activities.Statements.Rethrow> kullanılır.

## <a name="the-rethrow-activity"></a>Rethrow etkinliği

Etkinlik <xref:System.Activities.Statements.Rethrow> daha önce bir özel durum oluşturur. Bu etkinlik yalnızca etkinlikte bir <xref:System.Activities.Statements.Catch> işleyicide <xref:System.Activities.Statements.TryCatch> kullanılabilir.

### <a name="use-the-rethrow-activity-designer"></a>ReThrow Etkinlik Tasarımcısını Kullanma

Araç Kutusunun Hata İşleme kategorisindeki **Rethrow** etkinlik  **tasarımcısına erişin.** **Rethrow etkinlik** tasarımcısı Araç Kutusundan  sürüklenip bir içinde olduğu gibi İş Akışı Tasarımcısı yerleştirildikten sonra bu alan yüzeyine <xref:System.Activities.Statements.Sequence> bırakılır. Etkinlik tasarımcısı bırakarak, varsayılan <xref:System.Activities.Statements.Rethrow> **Throw DisplayName değerine sahip bir** etkinlik oluşturur. Değer Rethrow etkinlik tasarımcısının üst bilgisinde veya <xref:System.Activities.Activity.DisplayName%2A> özellik kılavuzundaki **DisplayName** kutusunda düzenlenebilir. 

### <a name="the-rethrow-properties"></a>Rethrow özellikleri

Aşağıdaki tabloda özellikler <xref:System.Activities.Statements.Rethrow> ve tasarımcıda nasıl kullanıldıkları açık bulunmaktadır:

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin isteğe bağlı kolay adını <xref:System.Activities.Statements.Rethrow> belirtir. Varsayılan değer Rethrow'dır.|

## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyon](../workflow-designer/collection-activity-designers.md)
- [Atmak](../workflow-designer/throw-activity-designer.md)
- [Trycatch](../workflow-designer/trycatch-activity-designer.md)
