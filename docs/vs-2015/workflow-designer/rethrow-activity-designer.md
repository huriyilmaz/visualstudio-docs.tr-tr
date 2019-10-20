---
title: Rethrow etkinlik Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c65469242a60c64d6f31bfaea4fdbbf2d5251a34
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663368"
---
# <a name="rethrow-activity-designer"></a>Rethrow Etkinlik Tasarımcısı
**Rethrow** etkinlik Tasarımcısı <xref:System.Activities.Statements.Rethrow> etkinlik oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-rethrow-activity"></a>Rethrow etkinliği
 @No__t_0 etkinliği daha önce oluşturulan bir özel durum oluşturur. Bu etkinlik, <xref:System.Activities.Statements.TryCatch> etkinliğinde yalnızca bir <xref:System.Activities.Statements.Catch> işleyicisinde kullanılabilir.

### <a name="using-the-rethrow-activity-designer"></a>ReThrow etkinlik tasarımcısını kullanma
 **Rethrow** etkinlik tasarımcısı, [!INCLUDE[wfd2](../includes/wfd2-md.md)] sol **tarafındaki araç** **kutusu** sekmesine tıklanarak erişilen **araç kutusunun** **hata işleme** kategorisinde bulunabilir (alternatif olarak,  **Görünüm** menüsü veya Ctrl + Alt + X.)

 **Rethrow** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, her durumda (örneğin, <xref:System.Activities.Statements.Sequence> gibi) [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyine bırakılabilir. Bu, varsayılan throw **DisplayName** 'i olan bir <xref:System.Activities.Statements.Rethrow> etkinliği oluşturur. @No__t_0 değeri **Rethrow** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-rethrow-properties"></a>Rethrow özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.Rethrow> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır.

|Özellik adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|@No__t_0 etkinliğinin isteğe bağlı kolay adını belirtir. Varsayılan değer Rethrow ' dir.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Koleksiyon](../workflow-designer/collection-activity-designers.md) [throw](../workflow-designer/throw-activity-designer.md) [](../workflow-designer/trycatch-activity-designer.md)