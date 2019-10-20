---
title: Etkinlik tasarımcısını Seç | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: daefc48cfff2c5c73d9ecf14316777becf4d83c5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672590"
---
# <a name="pick-activity-designer"></a>Pick Etkinlik Tasarımcısı
@No__t_0 etkinliği olay tabanlı denetim akışı sağlar. Etkinlik, bir tetikleme olayına yanıt olarak çeşitli dallardan birini yürütür.

## <a name="the-pick-activity"></a>Seçim etkinliği
 Bir <xref:System.Activities.Statements.Pick> etkinlik, bir tetikleyici olarak hizmet veren bazı gelen olayları nedeniyle <xref:System.Activities.Statements.Pick> etkinliğinin yürütebileceği <xref:System.Activities.Statements.PickBranch> nesneleri koleksiyonunu içerir. Bu şekilde [!INCLUDE[wfd1](../includes/wfd1-md.md)] olay tabanlı denetim akışı modelleme sağlar. Her <xref:System.Activities.Statements.PickBranch> bir <xref:System.Activities.Statements.PickBranch.Trigger%2A> ve <xref:System.Activities.Statements.PickBranch.Action%2A> içerir. @No__t_0 etkinliğin çalışmasının başlangıcında, <xref:System.Activities.Statements.PickBranch> öğelerinin tüm tetikleme etkinlikleri zamanlanır. İlk etkinlik tamamlandığında, ilgili eylem etkinliği zamanlanır ve diğer tüm tetikleyici etkinlikleri iptal edilir.

### <a name="how-to-use-the-pick-activity-designer"></a>Seçme etkinliği tasarımcısını kullanma
 **Seçim** etkinliği tasarımcısı, [!INCLUDE[wfd2](../includes/wfd2-md.md)] (alternatif olarak, **Görünüm** menüsünden **araç çubuğu** SEKMESINE tıklanarak veya Ctrl + Alt ' i seçerek **erişilen araç** **kutusunun** **Denetim akışı** kategorisinde bulunabilir. + X.)

 **Seçim** etkinliği Tasarımcısı **araç kutusundan** sürüklenip, örneğin bir **dizi** etkinlik tasarımcısı gibi etkinlik tasarımcılarının normalde yerleştirildiği [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyine bırakılabilir. @No__t_0 ' a geçirdikten sonra, varsayılan olarak iki boş <xref:System.Activities.Statements.PickBranch> etkinliği Branch1 ve branch2 görünen adları olan öğeler olarak içeren bir <xref:System.Activities.Statements.Pick> etkinliği oluşturur. Bu ilgili <xref:System.Activities.Statements.PickBranch.DisplayName%2A> özellik değerleri, **PickBranch** etkinlik Tasarımcısı üst bilgisinde veya her dal için **Özellikler** penceresinde düzenlenebilir.

 @No__t_1 nesnesinin koleksiyonuna <xref:System.Activities.Statements.PickBranch> etkinlik eklemenin iki yolu vardır: **araç kutusundan** **PickBranch** tasarımcısını sürükleyip bırakarak veya **seçim** tasarım yüzeyinde bağlam menüsünü kullanarak. Ayrıntılar için bkz. [PickBranch](../workflow-designer/pickbranch-activity-designer.md) konusu. Bir **seçim** etkinliği tasarımcısının içine yerleştirilebilecek tek öğenin bir **PickBranch** etkinlik Tasarımcısı olduğunu fark edersiniz.

### <a name="pick-activity-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı etkinlik özelliklerini seçme
 Aşağıdaki tabloda <xref:System.Activities.Statements.Pick> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzunda veya tasarımcı yüzeyinde düzenlenebilir.

|Özellik adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Üst bilgide <xref:System.Activities.Statements.Pick> etkinlik tasarımcısının kolay adını belirtir. Varsayılan değer, seçer. Değer, özellik kılavuzunda veya doğrudan etkinlik tasarımcısının üst bilgisinde düzenlenebilir.<br /><br /> @No__t_0 kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Çekme etkinliğini kullanarak](https://msdn.microsoft.com/library/b89be812-a247-4025-b0e3-ffb20db027a6) [Denetim akışı](../workflow-designer/control-flow-activity-designers.md) [çekme etkinliği](https://msdn.microsoft.com/library/b3e49b7f-0285-4720-8c09-11ae18f0d53e)