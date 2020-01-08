---
title: İş Akışı Tasarımcısı-throw etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 650082ab0e4f8576b7028b8011c88bf5d93b2afd
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593102"
---
# <a name="throw-activity-designer"></a>Throw Etkinlik Tasarımcısı

**Throw** etkinlik Tasarımcısı <xref:System.Activities.Statements.Throw> etkinlik oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-throw-activity"></a>Throw etkinliği

<xref:System.Activities.Statements.Throw> etkinliği bir özel durum oluşturur.

### <a name="using-the-throw-activity-designer"></a>Throw etkinlik tasarımcısını kullanma

**Araç kutusunun** **hata işleme** kategorisindeki **throw** etkinlik tasarımcısına erişin.

**Throw** etkinlik Tasarımcısı **araç kutusundan** sürüklenip İş Akışı Tasarımcısı yüzeyine, örneğin <xref:System.Activities.Statements.Sequence>içinde olduğu gibi, her yerde bırakılmış olarak bırakılabilir. Bu, varsayılan throw **DisplayName** 'i olan bir <xref:System.Activities.Statements.Throw> etkinliği oluşturur. <xref:System.Activities.Activity.DisplayName%2A> değeri, **throw** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir. <xref:System.Activities.Statements.Throw.Exception%2A> özelliği, özellik kılavuzunda düzenlenmelidir.

### <a name="the-throw-properties"></a>Throw özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.Throw> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Throw> etkinliğinin isteğe bağlı kolay adını belirtir. Varsayılan değer throw ' dir.|
|<xref:System.Activities.Statements.Throw.Exception%2A>|Doğru|Throw özel durumu. Bu özel durum <xref:System.Exception>türetmelidir. Özel durumu belirtmek için, özellik kılavuzuna bir Visual Basic ifadesi yazın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyon](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Throw Etkinlik Tasarımcısı](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)
