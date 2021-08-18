---
title: CancellationScope Etkinlik Tasarımcısı
description: CancellationScope etkinliğini oluşturmak ve yapılandırmak için İş Akışı Tasarımcısı 'de CancellationScope Etkinlik tasarımcısını nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 91eb31444a56d68f062f7909d9fb5de13d3f496d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122082614"
---
# <a name="cancellationscope-activity-designer"></a>CancellationScope Etkinlik Tasarımcısı

**CancellationScope** etkinlik Tasarımcısı bir etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.Activities.Statements.CancellationScope> .

## <a name="the-cancellationscope-activity"></a>CancellationScope etkinliği

<xref:System.Activities.Statements.CancellationScope>Etkinlik, bu etkinlik için yürütme ve iptal mantığı için bir etkinlik belirtmenize olanak tanır.

### <a name="using-the-cancellationscope-activity-designer"></a>CancellationScope Etkinlik tasarımcısını kullanma

**CancellationScope** etkinlik Tasarımcısı **araç kutusu** **işlem** kategorisinde bulunabilir. **Araç kutusunu** açmak Için iş akışı Tasarımcısı **araç kutusu** sekmesini seçin. Alternatif olarak, **Görünüm** menüsünden **araç kutusu** ' nu seçin veya **CTRL** + **alt** + **X** tuşlarına basın.

**CancellationScope** etkinlik Tasarımcısı **araç kutusu** 'ndan sürüklenebilir ve içindeki gibi etkinliklerin yerleştirildiği iş akışı Tasarımcısı yüzeyine bırakılabilir <xref:System.Activities.Statements.Sequence> . **CancellationScope** etkinlik Tasarımcısı ' nın atılması, <xref:System.Activities.Statements.CancellationScope> varsayılan CancellationScope olan bir etkinlik oluşturur <xref:System.Activities.Activity.DisplayName%2A> . <xref:System.Activities.Activity.DisplayName%2A> **CancellationScope** etkinlik Tasarımcısı üstbilgisindeki değeri düzenleyin. Bunu Özellik kılavuzunun **DisplayName** kutusunda da düzenleyebilirsiniz.

### <a name="the-cancellationscope-properties"></a>CancellationScope özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.CancellationScope> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. <xref:System.Activities.Activity.DisplayName%2A>Özellik, özellik kılavuzunda düzenlenebilir, ancak diğer özellikler iş akışı Tasarımcısı yüzeyinde düzenlenmelidir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin isteğe bağlı kolay adı <xref:System.Activities.Statements.CancellationScope> . Varsayılan değer CancellationScope ' dir. <xref:System.Activities.Activity.DisplayName%2A>Değer kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|Doğru|İptal mantığının sağlandığı etkinliği belirtir. Etkinliği eklemek için <xref:System.Activities.Statements.CancellationScope.Body%2A> , **araç kutusundan** bir etkinliği **CancellationScope** etkinlik Tasarımcısı ' nın **gövde** kutusuna bırakın. "Etkinliği buraya bırak" ipucu metnini ekleyin.|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|Doğru|İptal varsa yürütülen etkinliği belirtir. Etkinliği eklemek için <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> , **Toolbox** 'Tan bir etkinliği **CancellationScope** Etkinlik tasarımcısında **CancellationHandler** kutusuna bırakın. "Etkinliği buraya bırak" ipucu metnini ekleyin.|

## <a name="see-also"></a>Ayrıca bkz.

- [İşlem](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)
