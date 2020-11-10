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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9195fc95ac905213b048aa16882ea6584adacd33
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434122"
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
