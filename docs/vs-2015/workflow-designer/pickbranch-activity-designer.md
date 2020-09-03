---
title: PickBranch etkinlik Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c7c70aa8282fb8f50ed6faca5bcee3177ef81e15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672580"
---
# <a name="pickbranch-activity-designer"></a>PickBranch Etkinlik Tasarımcısı
, <xref:System.Activities.Statements.PickBranch> <xref:System.Activities.Statements.Pick> Gelen bir olay tarafından tetiklenebilecek bir etkinlik içindeki bir olay tabanlı yürütme yolu sağlar.

## <a name="pickbranch"></a>PickBranch
 <xref:System.Activities.Statements.PickBranch> nesneler <xref:System.Activities.Statements.Pick.Branches%2A> bir etkinlik koleksiyonunda bulunur <xref:System.Activities.Statements.Pick> . Her biri <xref:System.Activities.Statements.PickBranch> etkinliğin bir dalında bulunur <xref:System.Activities.Statements.Pick> ve tetikleyici olarak hizmet veren bazı gelen etkinlikler nedeniyle Yürütülebilirler. Bu şekilde, [!INCLUDE[wfd1](../includes/wfd1-md.md)] olay tabanlı denetim akışı modelleme sağlar. Her biri <xref:System.Activities.Statements.PickBranch> bir <xref:System.Activities.Statements.PickBranch.Trigger%2A> ve içerir <xref:System.Activities.Statements.PickBranch.Action%2A> .

### <a name="how-to-use-the-pick-activity-designer"></a>Seçme etkinliği tasarımcısını kullanma
 **PickBranch** Designer **, ' ın**araç **kutusu** sekmesine tıklanarak erişilen (alternatif olarak, **Control Flow** [!INCLUDE[wfd2](../includes/wfd2-md.md)] **Görünüm** menüsünden **araç çubuğu** ' nu veya Ctrl + Alt + X) denetim akış kategorisinde bulunabilir.

 <xref:System.Activities.Statements.PickBranch> **Branch1** ve **branch2** görünen adlarına sahip iki boş nesne <xref:System.Activities.Statements.Pick> , **çekme** etkinliği Tasarımcısı başlangıçta öğesine bırakıldığında bir etkinliğin öğeleri olarak varsayılan olarak oluşturulur [!INCLUDE[wfd2](../includes/wfd2-md.md)] . Bu ilgili <xref:System.Activities.Statements.PickBranch.DisplayName%2A> özellik değerleri, **PickBranch** Designer üst bilgisinde veya her dal için **Özellikler** penceresinde düzenlenebilir.

 Nesne koleksiyonuna nesne eklemenin iki yolu vardır <xref:System.Activities.Statements.PickBranch> <xref:System.Activities.Statements.Pick> : **araç kutusundan** **PickBranch** tasarımcısını sürükleyip bırakarak veya **seçim** tasarım yüzeyi içinden bağlam menüsünü kullanarak:

1. **PickBranch** Designer, <xref:System.Activities.Statements.PickBranch> **araç kutusundan** sürüklendiğinde ve yüzeyde bir **çekme** etkinliği tasarımcısının dallarından birine bırakıldığında bir oluşturur [!INCLUDE[wfd2](../includes/wfd2-md.md)] . Yeni <xref:System.Activities.Statements.PickBranch> nesneler, daha <xref:System.Activities.Statements.Pick> önce koleksiyonda bulunan mevcut öğelerin sol veya sağ tarafında tasarımcı içine yerleştirilebilir <xref:System.Activities.Statements.PickBranch> . Bir **PickBranch** tasarımcısını fareyle **seçim** tasarımcısına sürüklediğinizde, **seçim** Tasarımcısı, <xref:System.Activities.Statements.PickBranch> belirli bir fare yerleşimi için nereye ekleneceğini göstermek için dikey mavi gri bir bant kullanır.

2. Bağlam menüsünü almak ve yeni bir eklemek için **dal oluştur** ' u seçmek için etkinlik tasarımcısını **Seç** ( **PickBranch** Designer içinde değil) öğesine sağ tıklayın <xref:System.Activities.Statements.PickBranch> . Yeni öğesinin, <xref:System.Activities.Statements.PickBranch> seçme tasarımcısında var olan nesnelerin sağına eklendiğini unutmayın <xref:System.Activities.Statements.PickBranch> . **Pick**

   **PickBranch** Designer, üst bilgilerinin sağ tarafındaki çift yüzlere tıklanarak **tetikleyici** ve **eylem** kutularını açığa çıkarmak veya daraltılması için genişletilebilir. Etkinlikleri, <xref:System.Activities.Statements.PickBranch.Trigger%2A> <xref:System.Activities.Statements.PickBranch.Action%2A> <xref:System.Activities.Statements.PickBranch> tasarımcılarının **tetikleyici** ve **eylem** kutularına bırakarak her birini düzenleyin.

   <xref:System.Activities.Statements.PickBranch> <xref:System.Activities.Statements.Pick.Branches%2A> Bir nesne koleksiyonundaki nesneler <xref:System.Activities.Statements.Pick> , **seçim** Tasarımcısı içindeki yeni bir konuma sürükleyip bırakarak yeniden sıralanabilir. **Seçim** Tasarımcısı, <xref:System.Activities.Statements.PickBranch> belirli bir fare yerleşimi için nereye ekleneceğini göstermek için dikey mavi gri bir bant kullanır.

   Şunları silmenin iki yolu vardır <xref:System.Activities.Statements.PickBranch> :

3. **PickBranch** tasarımcısını seçin ve silin.

4. **PickBranch** tasarımcısını seçin, bağlam menüsünü almak için sağ tıklayın ve **Sil**' i seçin.

   , **Tetikleyicisinin** veya **eylem** kutularının içindeki etkinliklerden birini, yanlışlıkla bu etkinliklerden birini siler ve nesne değil, seçim **dalı** tasarımcısını seçmeye dikkat edin <xref:System.Activities.Statements.PickBranch> .

### <a name="pickbranch-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı PickBranch özellikleri
 Aşağıdaki tabloda en yararlı <xref:System.Activities.Statements.PickBranch> Özellikler gösterilmektedir ve içinde bunların nasıl kullanılacağı açıklanmaktadır [!INCLUDE[wfd2](../includes/wfd2-md.md)] .

|Özellik Adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|Yanlış|**PickBranch** tasarımcısının üst bilgisinde görünen kolay ad. Varsayılan değer daldır.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>Kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|Doğru|Her biri <xref:System.Activities.Statements.PickBranch> <xref:System.Activities.Statements.PickBranch.Trigger%2A> , çağırabilen bir eylem içerir <xref:System.Activities.Statements.PickBranch.Action%2A> .|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|Yanlış|Her biri <xref:System.Activities.Statements.PickBranch> <xref:System.Activities.Statements.PickBranch.Action%2A> tetikleniyorsa yürütülen bir içerir.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Çekme etkinliğini kullanarak](https://msdn.microsoft.com/library/b89be812-a247-4025-b0e3-ffb20db027a6) [Denetim akışı](../workflow-designer/control-flow-activity-designers.md) [çekme etkinliği](https://msdn.microsoft.com/library/b3e49b7f-0285-4720-8c09-11ae18f0d53e)