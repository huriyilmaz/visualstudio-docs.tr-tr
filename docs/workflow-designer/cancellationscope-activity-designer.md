---
title: İş Akışı Tasarımcısı-CancellationScope Etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a6d1067b529dffec5a4e6a1f21d5489c32311c07
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76112500"
---
# <a name="cancellationscope-activity-designer"></a>CancellationScope Etkinlik Tasarımcısı

**CancellationScope** etkinlik Tasarımcısı <xref:System.Activities.Statements.CancellationScope> etkinlik oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-cancellationscope-activity"></a>CancellationScope etkinliği

<xref:System.Activities.Statements.CancellationScope> etkinliği, bu etkinlik için yürütme ve iptal mantığı için bir etkinlik belirtmenize olanak tanır.

### <a name="using-the-cancellationscope-activity-designer"></a>CancellationScope Etkinlik tasarımcısını kullanma

**CancellationScope** etkinlik Tasarımcısı **araç kutusu** **işlem** kategorisinde bulunabilir. **Araç kutusunu**açmak Için iş akışı Tasarımcısı **araç kutusu** sekmesini seçin. Alternatif olarak, **Görünüm** menüsünden **araç kutusu** ' nu seçin veya **CTRL**+**alt**+**X**tuşuna basın.

**CancellationScope** etkinlik Tasarımcısı, **araç kutusu** 'ndan sürüklenip iş akışı Tasarımcısı, <xref:System.Activities.Statements.Sequence>içinde olduğu gibi etkinliklerin yerleştirildiği yüzeyine bırakılabilir. **CancellationScope** etkinlik Tasarımcısı ' nın atılması, <xref:System.Activities.Activity.DisplayName%2A> varsayılan bir CancellationScope <xref:System.Activities.Statements.CancellationScope> etkinlik oluşturur. **CancellationScope** etkinlik tasarımcısı üstbilgisindeki <xref:System.Activities.Activity.DisplayName%2A> değerini düzenleyin. Bunu Özellik kılavuzunun **DisplayName** kutusunda da düzenleyebilirsiniz.

### <a name="the-cancellationscope-properties"></a>CancellationScope özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.CancellationScope> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. <xref:System.Activities.Activity.DisplayName%2A> özelliği özellik kılavuzunda düzenlenebilir, ancak diğer özellikler İş Akışı Tasarımcısı yüzeyinde düzenlenmelidir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.CancellationScope> etkinliğinin isteğe bağlı kolay adı. Varsayılan değer CancellationScope ' dir. <xref:System.Activities.Activity.DisplayName%2A> değeri kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|Doğru|İptal mantığının sağlandığı etkinliği belirtir. <xref:System.Activities.Statements.CancellationScope.Body%2A> etkinliğini eklemek için, **araç kutusundan** bir etkinliği **CancellationScope** etkinlik Tasarımcısı ' nın **gövde** kutusuna bırakın. "Etkinliği buraya bırak" ipucu metnini ekleyin.|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|Doğru|İptal varsa yürütülen etkinliği belirtir. <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> etkinliğini eklemek için, **Toolbox** 'tan bir etkinliği **CancellationScope** Activity Designer 'daki **CancellationHandler** kutusuna bırakın. "Etkinliği buraya bırak" ipucu metnini ekleyin.|

## <a name="see-also"></a>Ayrıca bkz.

- [İşlem](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)
