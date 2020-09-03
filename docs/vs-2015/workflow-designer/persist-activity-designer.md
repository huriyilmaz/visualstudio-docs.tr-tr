---
title: Etkinlik tasarımcısını Sürdür | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 60a63dd4036863641646e85a89f5018cba786802
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672620"
---
# <a name="persist-activity-designer"></a>Persist Etkinlik Tasarımcısı
**Kalıcı** etkinlik Tasarımcısı, etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.Activities.Statements.Persist> .

## <a name="the-persist-activity"></a>Kalıcı etkinlik
 <xref:System.Activities.Statements.Persist>Etkinlik, mümkünse bir iş akışını diske kaydeder. <xref:System.Activities.Statements.Persist>Etkinlik, örneğin bir etkinlik içinde, kalıcılık olmayan bir bölgede yürütülemez <xref:System.Activities.Statements.TransactionScope> . <xref:System.Activities.Statements.Persist>Kalıcı olmayan bir kapsamda etkinlik kullanıyorsanız, çalışma zamanında bir özel durum oluşturulur.

### <a name="using-the-persist-activity-designer"></a>Kalıcı etkinlik tasarımcısını kullanma
 **Kalıcı** etkinlik **Tasarımcısı araç kutusu sekmesine** tıklanarak erişilen (alternatif olarak, **Görünüm** menüsünden **araç kutusu** ' nu veya Ctrl + Alt + X ' i seçerek **),** **çalışma alanının çalışma zamanı** kategorisinde bulunabilir.

 **Kalıcı** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, ancak [!INCLUDE[wfd2](../includes/wfd2-md.md)] içinde olduğu gibi etkinliklerin genellikle yerleştirildiği yüzeye bırakılabilir <xref:System.Activities.Statements.Sequence> . Bu <xref:System.Activities.Statements.Persist> , varsayılan olarak **görünmeyen** bir etkinlik oluşturur. , <xref:System.Activities.Activity.DisplayName%2A> **Kalıcı** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-persist-properties"></a>Devam eden özellikler
 Aşağıdaki tabloda <xref:System.Activities.Statements.Persist> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzunda düzenlenebilir ve bazıları [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyinde düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin kolay adı <xref:System.Activities.Statements.Persist> . Varsayılan değer korunur. Görünen ad kesinlikle gerekli olmasa da, bir görünen ad kullanmak en iyi uygulamadır.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Çalışma zamanı](../workflow-designer/runtime-activity-designers.md) [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)