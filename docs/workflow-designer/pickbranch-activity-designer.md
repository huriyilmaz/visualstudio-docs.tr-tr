---
title: İş Akışı Tasarımcısı-PickBranch etkinlik Tasarımcısı
description: PickBranch etkinlik Tasarımcısı 'nın, gelen bir olay tarafından tetiklenebilecek bir çekme etkinliği içinde, olay tabanlı bir yürütme yolu sağladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9d3ac314d5f8eb7980bdf5102d871546d3167141
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968677"
---
# <a name="pickbranch-activity-designer"></a>PickBranch Etkinlik Tasarımcısı

, <xref:System.Activities.Statements.PickBranch> <xref:System.Activities.Statements.Pick> Gelen bir olay tarafından tetiklenebilecek bir etkinlik içindeki bir olay tabanlı yürütme yolu sağlar.

## <a name="pickbranch"></a>PickBranch

<xref:System.Activities.Statements.PickBranch> nesneler <xref:System.Activities.Statements.Pick.Branches%2A> bir etkinlik koleksiyonunda bulunur <xref:System.Activities.Statements.Pick> . Her biri <xref:System.Activities.Statements.PickBranch> etkinliğin bir dalında bulunur <xref:System.Activities.Statements.Pick> ve tetikleyici olarak hizmet veren bazı gelen etkinlikler nedeniyle Yürütülebilirler. Bu şekilde İş Akışı Tasarımcısı, olay tabanlı denetim akışı modelleme sağlar. Her biri <xref:System.Activities.Statements.PickBranch> bir <xref:System.Activities.Statements.PickBranch.Trigger%2A> ve içerir <xref:System.Activities.Statements.PickBranch.Action%2A> .

### <a name="how-to-use-the-pick-activity-designer"></a>Seçme etkinliği tasarımcısını kullanma

**Araç kutusunun** **Denetim akışı** kategorisindeki **PickBranch** tasarımcısına erişin.

<xref:System.Activities.Statements.PickBranch> **Branch1** ve **branch2** görünen adlarına sahip iki boş nesne, <xref:System.Activities.Statements.Pick> **çekme** etkinliği Tasarımcısı başlangıçta iş akışı Tasarımcısı bir etkinliğin öğeleri olarak oluşturulur. Bu ilgili <xref:System.Activities.Statements.PickBranch.DisplayName%2A> özellik değerleri, **PickBranch** Designer üst bilgisinde veya her dal için **Özellikler** penceresinde düzenlenebilir.

Nesne koleksiyonuna nesne eklemenin iki yolu vardır <xref:System.Activities.Statements.PickBranch> <xref:System.Activities.Statements.Pick> : **araç kutusundan** **PickBranch** tasarımcısını sürükleyip bırakarak veya tasarım yüzeyi içinden sağ tıklama menüsünü kullanarak: 

- **PickBranch** Designer, <xref:System.Activities.Statements.PickBranch> **araç kutusundan** sürüklendiğinde ve iş akışı Tasarımcısı yüzeyinde bir **seçim** etkinliği tasarımcısının dallarından birine bırakıldığında bir oluşturur. Yeni <xref:System.Activities.Statements.PickBranch> nesneler, daha <xref:System.Activities.Statements.Pick> önce koleksiyonda bulunan mevcut öğelerin sol veya sağ tarafında tasarımcı içine yerleştirilebilir <xref:System.Activities.Statements.PickBranch> . Bir **PickBranch** tasarımcısını fareyle **seçim** tasarımcısına sürüklediğinizde, **seçim** Tasarımcısı, <xref:System.Activities.Statements.PickBranch> belirli bir fare yerleşimi için nereye ekleneceğini göstermek için dikey mavi gri bir bant kullanır.

- Bir bağlam menüsü edinmek ve yeni bir eklemek için **dal oluştur** ' u seçerek etkinlik tasarımcısını **Seç** ( **PickBranch** Designer içinde değil) öğesine sağ tıklayın <xref:System.Activities.Statements.PickBranch> . Yeni öğesinin, <xref:System.Activities.Statements.PickBranch> seçme tasarımcısında var olan nesnelerin sağına eklendiğini unutmayın <xref:System.Activities.Statements.PickBranch> . 

**PickBranch** Designer, üst bilgilerinin sağ tarafındaki çift yüzlere tıklanarak **tetikleyici** ve **eylem** kutularını açığa çıkarmak veya daraltılması için genişletilebilir. Etkinlikleri, <xref:System.Activities.Statements.PickBranch.Trigger%2A> <xref:System.Activities.Statements.PickBranch.Action%2A> <xref:System.Activities.Statements.PickBranch> tasarımcılarının **tetikleyici** ve **eylem** kutularına bırakarak her birini düzenleyin.

<xref:System.Activities.Statements.PickBranch> <xref:System.Activities.Statements.Pick.Branches%2A> Bir nesne koleksiyonundaki nesneler <xref:System.Activities.Statements.Pick> , **seçim** Tasarımcısı içindeki yeni bir konuma sürükleyip bırakarak yeniden sıralanabilir. **Seçim** Tasarımcısı, <xref:System.Activities.Statements.PickBranch> belirli bir fare yerleşimi için nereye ekleneceğini göstermek için dikey mavi gri bir bant kullanır.

Şunları silmenin iki yolu vardır <xref:System.Activities.Statements.PickBranch> :

- **PickBranch** tasarımcısını seçin ve silin.
- **PickBranch** tasarımcısını seçin, bağlam menüsünü almak için sağ tıklayın ve **Sil**' i seçin.

, **Tetikleyicisinin** veya **eylem** kutularının içindeki etkinliklerden birini, yanlışlıkla bu etkinliklerden birini siler ve nesne değil, seçim **dalı** tasarımcısını seçmeye dikkat edin <xref:System.Activities.Statements.PickBranch> .

### <a name="pickbranch-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı PickBranch özellikleri

Aşağıdaki tabloda en yararlı <xref:System.Activities.Statements.PickBranch> Özellikler gösterilmektedir ve bunların iş akışı Tasarımcısı nasıl kullanılacağı açıklanmaktadır.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|Yanlış|**PickBranch** tasarımcısının üst bilgisinde görünen kolay ad. Varsayılan değer daldır.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>Kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|Doğru|Her biri <xref:System.Activities.Statements.PickBranch> <xref:System.Activities.Statements.PickBranch.Trigger%2A> , çağırabilen bir eylem içerir <xref:System.Activities.Statements.PickBranch.Action%2A> .|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|Yanlış|Her biri <xref:System.Activities.Statements.PickBranch> <xref:System.Activities.Statements.PickBranch.Action%2A> tetikleniyorsa yürütülen bir içerir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Denetim akışı](../workflow-designer/control-flow-activity-designers.md)
- [Pick Etkinliği](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Pick Etkinliği Kullanma](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)