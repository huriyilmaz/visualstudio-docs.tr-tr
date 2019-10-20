---
title: İş Akışı Tasarımcısı-PickBranch etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a43fa99c9f5fe4fbb3cfe336efb983fced655f2a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650064"
---
# <a name="pickbranch-activity-designer"></a>PickBranch Etkinlik Tasarımcısı

@No__t_0, gelen bir olay tarafından tetiklenebilecek bir <xref:System.Activities.Statements.Pick> etkinliği içinde yürütülen olay tabanlı bir yol sağlar.

## <a name="pickbranch"></a>PickBranch

<xref:System.Activities.Statements.PickBranch> nesneler bir <xref:System.Activities.Statements.Pick> etkinliğinin <xref:System.Activities.Statements.Pick.Branches%2A> koleksiyonunda bulunur. Her bir <xref:System.Activities.Statements.PickBranch>, <xref:System.Activities.Statements.Pick> etkinliğinin bir dalında bulunur ve tetikleyici olarak hizmet veren bazı gelen etkinlikler nedeniyle Yürütülebilirler. Bu şekilde İş Akışı Tasarımcısı, olay tabanlı denetim akışı modelleme sağlar. Her <xref:System.Activities.Statements.PickBranch> bir <xref:System.Activities.Statements.PickBranch.Trigger%2A> ve <xref:System.Activities.Statements.PickBranch.Action%2A> içerir.

### <a name="how-to-use-the-pick-activity-designer"></a>Seçme etkinliği tasarımcısını kullanma

**Araç kutusunun** **Denetim akışı** kategorisindeki **PickBranch** tasarımcısına erişin.

**Branch1** ve **branch2** görünen adları olan iki boş <xref:System.Activities.Statements.PickBranch> nesnesi, **çekme** etkinliği Tasarımcısı başlangıçta iş akışı Tasarımcısı bırakıldığında varsayılan olarak bir <xref:System.Activities.Statements.Pick> etkinliğinin öğeleri olarak oluşturulur. Bu ilgili <xref:System.Activities.Statements.PickBranch.DisplayName%2A> özellik değerleri, **PickBranch** Designer üst bilgisinde veya her dala ait **Özellikler** penceresinde düzenlenebilir.

@No__t_1 nesnesinin koleksiyonuna <xref:System.Activities.Statements.PickBranch> nesneleri eklemenin iki yolu vardır: **araç kutusundan** **PickBranch** tasarımcısını sürükleyip bırakarak veya **seçme** tasarım yüzeyinde sağ tıklama menüsünü kullanarak:

- **PickBranch** Tasarımcısı **araç kutusundan** sürüklendiğinde bir <xref:System.Activities.Statements.PickBranch> oluşturur ve iş akışı Tasarımcısı yüzeyinde bir **seçim** etkinliği tasarımcısının dallarından birine bırakılır. Yeni <xref:System.Activities.Statements.PickBranch> nesneleri, koleksiyonda bulunan mevcut <xref:System.Activities.Statements.PickBranch> öğelerinin soluna veya sağına <xref:System.Activities.Statements.Pick> tasarımcı içine yerleştirilebilir. Bir **PickBranch** tasarımcısını fareyle **seçim** tasarımcısına sürüklediğinizde, **seçim** Tasarımcısı, belirli bir fare yerleşimi için <xref:System.Activities.Statements.PickBranch> eklendiğini göstermek için dikey mavi gri bant kullanır.

- Yeni bir <xref:System.Activities.Statements.PickBranch> eklemek için, bir bağlam menüsü edinmek ve **dal oluştur** ' u seçmek Için, **seçme** etkinlik Tasarımcısı ' na sağ tıklayın ( **PickBranch** Designer içinde değil). Yeni <xref:System.Activities.Statements.PickBranch>, **seçme** tasarımcısında var olan <xref:System.Activities.Statements.PickBranch> nesnelerinin sağına eklendiğini unutmayın.

**PickBranch** Designer, üst bilgilerinin sağ tarafındaki çift yüzlere tıklanarak **tetikleyici** ve **eylem** kutularını açığa çıkarmak veya daraltılması için genişletilebilir. Etkinlikleri tasarımcılarının **tetikleyici** ve **eylem** kutularına bırakarak her <xref:System.Activities.Statements.PickBranch> <xref:System.Activities.Statements.PickBranch.Trigger%2A> ve <xref:System.Activities.Statements.PickBranch.Action%2A> düzenleyin.

Bir <xref:System.Activities.Statements.Pick> nesnesinin <xref:System.Activities.Statements.Pick.Branches%2A> koleksiyonundaki <xref:System.Activities.Statements.PickBranch> nesneleri, **seçim** Tasarımcısı içindeki yeni bir konuma sürükleyip bırakarak yeniden sıralanabilir. **Seçim** Tasarımcısı, belirli bir fare yerleşimi için <xref:System.Activities.Statements.PickBranch> eklendiğini göstermek için dikey mavi gri bir bant kullanır.

@No__t_0 silmenin iki yolu vardır:

- **PickBranch** tasarımcısını seçin ve silin.
- **PickBranch** tasarımcısını seçin, bağlam menüsünü almak için sağ tıklayın ve **Sil**' i seçin.

Tasarımcı veya **eylem** kutularının içindeki etkinliklerden birini **seçerek, <xref:System.Activities.Statements.PickBranch>** nesnesinden birini değil, **PickBranch** tasarımcısını seçtiğinizden emin olun.

### <a name="pickbranch-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı PickBranch özellikleri

Aşağıdaki tabloda en yararlı <xref:System.Activities.Statements.PickBranch> özellikleri gösterilmektedir ve bunların İş Akışı Tasarımcısı nasıl kullanılacağı açıklanmaktadır.

|Özellik adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|**PickBranch** tasarımcısının üst bilgisinde görünen kolay ad. Varsayılan değer daldır.<br /><br /> @No__t_0 kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|Doğru|Her <xref:System.Activities.Statements.PickBranch>, <xref:System.Activities.Statements.PickBranch.Action%2A> çağırabilen bir <xref:System.Activities.Statements.PickBranch.Trigger%2A> eylemi içerir.|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|Her <xref:System.Activities.Statements.PickBranch> tetikleniyorsa yürütülen bir <xref:System.Activities.Statements.PickBranch.Action%2A> içerir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Denetim Akışı](../workflow-designer/control-flow-activity-designers.md)
- [Pick Etkinliği](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Pick Etkinliği Kullanma](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)