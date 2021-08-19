---
title: CompensableActivity Etkinlik Tasarımcısı
description: CompensableActivity etkinliği oluşturmak ve yapılandırmak için İş Akışı Tasarımcısı'da CompensableActivity etkinlik tasarımcısını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: b3334b2be145dd01bd89fcc0b0d792238e9a684f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122155310"
---
# <a name="compensableactivity-activity-designer"></a>CompensableActivity Etkinlik Tasarımcısı

**CompensableActivity etkinlik** tasarımcısı, etkinlik oluşturmak ve yapılandırmak için <xref:System.Activities.Statements.CompensableActivity> kullanılır.

## <a name="the-compensableactivity-activity"></a>CompensableActivity Etkinliği
 , <xref:System.Activities.Statements.CompensableActivity> başarıyla tamamlandıktan sonra onaylanmasını veya telafi edile bir iş birimini tanımlar.

### <a name="using-the-compensableactivity-activity-designer"></a>CompensableActivity Etkinlik Tasarımcısını Kullanma
 **CompensableActivity** etkinlik tasarımcısı, Araç Kutusunun **İşlem** **kategorisinde bulunabilir.** Araç **Kutusu'nı** açmak **için, araç** kutusunun sol tarafındaki Araç Kutusu İş Akışı Tasarımcısı. Alternatif olarak Görünüm **menüsünden Araç** Kutusu'nı **seçin** veya **Ctrl** Alt X + **tuşlarına** + **basın.**

 **CompensableActivity** etkinlik tasarımcısı Araç Kutusundan **sürüklenebilir** ve İş Akışı Tasarımcısı bırakılır. Etkinlik tasarımcısını bir içinde <xref:System.Activities.Statements.Sequence> bırakın. Etkinlik tasarımcısını bırakarak, <xref:System.Activities.Statements.CompensableActivity> <xref:System.Activities.Activity.DisplayName%2A> compensableActivity varsayılan değerine sahip bir etkinlik oluşturur. <xref:System.Activities.Activity.DisplayName%2A> **CompensableActivity** etkinlik tasarımcısının üst bilgisinde değerini düzenleyin. Özellik kılavuzunda **DisplayName kutusunda** da düzenlenebilir.

### <a name="the-compensableactivity-properties"></a>CompensableActivity Özellikleri
 Aşağıdaki tablo, <xref:System.Activities.Statements.CompensableActivity> özellikleri gösterir ve tasarımcıda nasıl kullanıldıklarını açıklar. ve <xref:System.Activities.Activity.DisplayName%2A> <xref:System.Activities.Activity%601.Result%2A> özelliği özellik kılavuzunda düzenlenebilir, ancak diğer özelliklerin İş Akışı Tasarımcısı düzenlenemez.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin isteğe bağlı kolay <xref:System.Activities.Statements.CompensableActivity> adı. CompensableActivity varsayılandır.|
|<xref:System.Activities.Activity%601.Result%2A>|Yanlış|değerinin dönüş değerini <xref:System.Activities.Statements.CompensableActivity> belirtir. Bu özellik, özellik kılavuzunda düzenlenemez.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|Doğru|Telafi, iptal ve onay mantığının sağlandı olduğu etkinliği belirtir. Etkinliği eklemek <xref:System.Activities.Statements.CompensableActivity.Body%2A> için Araç Kutusundan  **CompensableActivity** etkinlik tasarımcısının Gövde kutusuna bir etkinlik bırakın.  "Etkinliği buraya bırak" ipucu metnini ekleyin.|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|Yanlış|İptal olduğunda yürütülen etkinliği belirtir. Etkinliği eklemek için Araç Kutusundan **CompensableActivity** etkinlik tasarımcısının **CancellationHandler** kutusuna tasarımcısını bırakın.  "Etkinliği Buraya Bırak" ipucu metni ekleyin.|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|Yanlış|Etkinlik için telafi yapmak için yürütülecek etkinliği <xref:System.Activities.Statements.CompensableActivity.Body%2A> belirtir. Bu işleyici etkinlik kullanılarak açıkça <xref:System.Activities.Statements.Compensate> çağrılabilir.<br /><br /> Etkinliği eklemek için Araç Kutusu'nda etkinlik **tasarımcısını** **CompensableActivity** etkinlik tasarımcısının **CompensationHandler** kutusuna bırakın. "Etkinliği Buraya Bırak" ipucu metni ekleyin.|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|Yanlış|Etkinliği onaylarken yürütülecek etkinliği <xref:System.Activities.Statements.CompensableActivity.Body%2A> belirtir. Bu işleyici etkinlik kullanılarak açıkça <xref:System.Activities.Statements.Confirm> çağrılabilir.<br /><br /> Etkinliği eklemek için Araç Kutusu'nda etkinlik **tasarımcısını** **CompensableActivity** etkinlik tasarımcısının **ConfirmationHandler** kutusuna bırakın. "Etkinliği Buraya Bırak" ipucu metni ekleyin.|

## <a name="see-also"></a>Ayrıca bkz.

- [İşlem](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)
