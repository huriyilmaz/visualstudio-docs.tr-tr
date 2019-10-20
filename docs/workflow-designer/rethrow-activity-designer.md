---
title: İş Akışı Tasarımcısı-Rethrow etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d015ad500537a17cfc2c48c8076df43a38534ea
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650013"
---
# <a name="rethrow-activity-designer"></a>Rethrow Etkinlik Tasarımcısı

**Rethrow** etkinlik Tasarımcısı <xref:System.Activities.Statements.Rethrow> etkinlik oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-rethrow-activity"></a>Rethrow etkinliği

@No__t_0 etkinliği daha önce oluşturulan bir özel durum oluşturur. Bu etkinlik, <xref:System.Activities.Statements.TryCatch> etkinliğinde yalnızca bir <xref:System.Activities.Statements.Catch> işleyicisinde kullanılabilir.

### <a name="use-the-rethrow-activity-designer"></a>ReThrow etkinlik tasarımcısını kullanma

**Araç kutusunun** **hata Işleme** kategorisindeki **Rethrow** etkinlik tasarımcısına erişin. **Rethrow** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, her durumda (örneğin, <xref:System.Activities.Statements.Sequence> gibi) iş akışı Tasarımcısı yüzeyine bırakılabilir. Etkinlik Tasarımcısı ' nın atılması, varsayılan olarak throw **DisplayName** ile bir <xref:System.Activities.Statements.Rethrow> etkinliği oluşturur. @No__t_0 değeri **Rethrow** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-rethrow-properties"></a>Rethrow özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.Rethrow> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır:

|Özellik adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|@No__t_0 etkinliğinin isteğe bağlı kolay adını belirtir. Varsayılan değer Rethrow ' dir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyon](../workflow-designer/collection-activity-designers.md)
- [Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)