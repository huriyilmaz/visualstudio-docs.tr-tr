---
title: CancellationScope etkinlik tasarımcısı
description: CancellationScope etkinliği oluşturmak ve yapılandırmak için İş Akışı Tasarımcısı'da CancellationScope etkinlik tasarımcısını nasıl kullanabileceğiniz hakkında bilgi öğrenin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633726"
---
# <a name="cancellationscope-activity-designer"></a>CancellationScope Etkinlik Tasarımcısı

**CancellationScope etkinlik** tasarımcısı, etkinlik oluşturmak ve yapılandırmak için <xref:System.Activities.Statements.CancellationScope> kullanılır.

## <a name="the-cancellationscope-activity"></a>CancellationScope Etkinliği

Etkinlik, <xref:System.Activities.Statements.CancellationScope> bu etkinlik için yürütme ve iptal mantığı için bir etkinlik belirtmenize olanak sağlar.

### <a name="using-the-cancellationscope-activity-designer"></a>CancellationScope Etkinlik Tasarımcısını Kullanma

**CancellationScope** etkinlik tasarımcısı, Araç **Kutusu'nda İşlem** **kategorisinde bulunabilir.** Araç **Kutusu'nı** açmak için, **dosyanın** Araç Kutusu İş Akışı Tasarımcısı. Alternatif olarak Görünüm **menüsünden Araç** Kutusu'nı **seçin** veya **Ctrl** Alt X + **tuşlarına** + **basın.**

**CancellationScope** etkinlik tasarımcısı **Toolbox'tan** sürüklenip bir içinde olduğu gibi İş Akışı Tasarımcısı yerleştirildikten sonra bu alan yüzeyine <xref:System.Activities.Statements.Sequence> bırakılır. **CancellationScope etkinlik tasarımcısını** bırakarak, <xref:System.Activities.Statements.CancellationScope> cancellationScope varsayılan değeriyle <xref:System.Activities.Activity.DisplayName%2A> bir etkinlik oluşturur. <xref:System.Activities.Activity.DisplayName%2A>CancellationScope etkinlik tasarımcısının üst **bilgisinde değerini** düzenleyin. Ayrıca, özellik kılavuzunda **DisplayName** kutusunda da düzenleyebilirsiniz.

### <a name="the-cancellationscope-properties"></a>CancellationScope Özellikleri

Aşağıdaki tablo, <xref:System.Activities.Statements.CancellationScope> özellikleri gösterir ve tasarımcıda nasıl kullanıldıklarını açıklar. özelliği <xref:System.Activities.Activity.DisplayName%2A> özellik kılavuzunda düzenlenebilir, ancak diğer özelliklerin tek bir yüzeyde İş Akışı Tasarımcısı gerekir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin isteğe bağlı kolay <xref:System.Activities.Statements.CancellationScope> adı. CancellationScope varsayılandır. Değer <xref:System.Activities.Activity.DisplayName%2A> kesinlikle gerekli değildir ancak bir değer kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|Doğru|İptal mantığının sağlanacak etkinliğini belirtir. Etkinliği eklemek <xref:System.Activities.Statements.CancellationScope.Body%2A> için Araç Kutusundan **CancellationScope etkinlik** tasarımcısının Gövde kutusuna bir **etkinlik** bırakın.  "Etkinliği Buraya Bırak" ipucu metnini ekleyin.|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|Doğru|İptal varsa yürütülen etkinliği belirtir. Etkinliği eklemek <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> için, Araç Kutusundan **CancellationScope** etkinlik tasarımcısında **CancellationHandler** **kutusuna bir** etkinlik bırakın. "Etkinliği Buraya Bırak" ipucu metnini ekleyin.|

## <a name="see-also"></a>Ayrıca bkz.

- [İşlem](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)
