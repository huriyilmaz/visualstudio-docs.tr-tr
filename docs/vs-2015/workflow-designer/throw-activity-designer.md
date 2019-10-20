---
title: Throw etkinlik Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1855daa5016241fb6eb04f05d7218e02083fc0a8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655159"
---
# <a name="throw-activity-designer"></a>Throw Etkinlik Tasarımcısı
**Throw** etkinlik Tasarımcısı <xref:System.Activities.Statements.Throw> etkinlik oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-throw-activity"></a>Throw etkinliği
 @No__t_0 etkinliği bir özel durum oluşturur.

### <a name="using-the-throw-activity-designer"></a>Throw etkinlik tasarımcısını kullanma
 **Throw** etkinliği tasarımcısı, [!INCLUDE[wfd2](../includes/wfd2-md.md)] sol tarafındaki araç **kutusu** sekmesine tıklanarak erişilen **araç kutusunun** **hata Işleme** kategorisinde bulunabilir (alternatif olarak, görünümden **araç çubuğu** ' nu seçin).menü veya Ctrl + Alt + X.)

 **Throw** etkinlik Tasarımcısı **araç kutusundan** sürüklenip [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyine, örneğin <xref:System.Activities.Statements.Sequence> içinde olduğu gibi, her yerde bırakılmış olarak bırakılabilir. Bu, varsayılan throw **DisplayName** 'i olan bir <xref:System.Activities.Statements.Throw> etkinliği oluşturur. @No__t_0 değeri, **throw** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir. @No__t_0 özelliği, özellik kılavuzunda düzenlenmelidir.

### <a name="the-throw-properties"></a>Throw özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.Throw> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır.

|Özellik adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|@No__t_0 etkinliğinin isteğe bağlı kolay adını belirtir. Varsayılan değer throw ' dir.|
|<xref:System.Activities.Statements.Throw.Exception%2A>|Doğru|Throw özel durumu. Bu özel durum <xref:System.Exception> türetmelidir. Özel durumu belirtmek için, özellik kılavuzuna bir Visual Basic ifadesi yazın.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Koleksiyon](../workflow-designer/collection-activity-designers.md) [Rethrow](../workflow-designer/rethrow-activity-designer.md) [throw etkinlik Tasarımcısı](../workflow-designer/throw-activity-designer.md) [TryCatch](../workflow-designer/trycatch-activity-designer.md)