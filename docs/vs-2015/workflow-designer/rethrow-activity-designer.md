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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663368"
---
# <a name="rethrow-activity-designer"></a>Rethrow Etkinlik Tasarımcısı
**Rethrow** etkinlik Tasarımcısı, etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.Activities.Statements.Rethrow> .

## <a name="the-rethrow-activity"></a>Rethrow etkinliği
 <xref:System.Activities.Statements.Rethrow>Etkinlik daha önce oluşturulan bir özel durum oluşturur. Bu etkinlik yalnızca <xref:System.Activities.Statements.Catch> etkinlikteki bir işleyicide kullanılabilir <xref:System.Activities.Statements.TryCatch> .

### <a name="using-the-rethrow-activity-designer"></a>ReThrow etkinlik tasarımcısını kullanma
 **Rethrow** etkinlik Tasarımcısı, ' ın sol tarafındaki araç **kutusu** sekmesine tıklanarak erişilen **araç kutusunun** **hata Işleme** kategorisinde bulunabilir [!INCLUDE[wfd2](../includes/wfd2-md.md)] (alternatif olarak, **Görünüm** menüsünden **araç çubuğu** ' nu veya Ctrl + Alt + X ' i seçin.)

 **Rethrow** etkinlik Tasarımcısı, **araç kutusundan** sürüklenip, ancak [!INCLUDE[wfd2](../includes/wfd2-md.md)] içinde olduğu gibi etkinliklerin genellikle yerleştirildiği yüzeye bırakılabilir <xref:System.Activities.Statements.Sequence> . Bu <xref:System.Activities.Statements.Rethrow> , throw öğesinin varsayılan **DisplayName** ile bir etkinlik oluşturur. <xref:System.Activities.Activity.DisplayName%2A>Değer **Rethrow** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-rethrow-properties"></a>Rethrow özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.Rethrow> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır.

|Özellik Adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin isteğe bağlı kolay adını belirtir <xref:System.Activities.Statements.Rethrow> . Varsayılan değer Rethrow ' dir.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Koleksiyon](../workflow-designer/collection-activity-designers.md) [throw](../workflow-designer/throw-activity-designer.md) [TryCatch](../workflow-designer/trycatch-activity-designer.md)