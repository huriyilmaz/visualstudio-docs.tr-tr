---
title: İş Akışı Tasarımcısı-Rethrow etkinlik Tasarımcısı
description: Rethrow etkinliği hakkında bilgi edinin ve Rethrow etkinlik Tasarımcısı 'nı kullanarak yeniden oluşturma etkinliği oluşturun ve yapılandırın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2e3615c73583e8c5c313d23fd5f9aa6d9fcd5ff4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847329"
---
# <a name="rethrow-activity-designer"></a>Rethrow Etkinlik Tasarımcısı

**Rethrow** etkinlik Tasarımcısı, etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.Activities.Statements.Rethrow> .

## <a name="the-rethrow-activity"></a>Rethrow etkinliği

<xref:System.Activities.Statements.Rethrow>Etkinlik daha önce oluşturulan bir özel durum oluşturur. Bu etkinlik yalnızca <xref:System.Activities.Statements.Catch> etkinlikteki bir işleyicide kullanılabilir <xref:System.Activities.Statements.TryCatch> .

### <a name="use-the-rethrow-activity-designer"></a>ReThrow etkinlik tasarımcısını kullanma

**Araç kutusunun** **hata Işleme** kategorisindeki **Rethrow** etkinlik tasarımcısına erişin. **Rethrow** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, örneğin içinde olduğu gibi etkinliklerin genellikle yerleştirildiği iş akışı Tasarımcısı yüzeyine bırakılabilir <xref:System.Activities.Statements.Sequence> . Etkinlik Tasarımcısı ' nın atılması, <xref:System.Activities.Statements.Rethrow> throw öğesinin varsayılan **DisplayName** değeriyle bir etkinlik oluşturur. <xref:System.Activities.Activity.DisplayName%2A>Değer **Rethrow** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-rethrow-properties"></a>Rethrow özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.Rethrow> Özellikler gösterilmektedir ve tasarımcıda nasıl kullanıldıkları açıklanmıştır:

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin isteğe bağlı kolay adını belirtir <xref:System.Activities.Statements.Rethrow> . Varsayılan değer Rethrow ' dir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyon](../workflow-designer/collection-activity-designers.md)
- [Yaratır](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)
