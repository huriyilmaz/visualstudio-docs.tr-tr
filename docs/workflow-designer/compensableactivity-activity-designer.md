---
title: CompensableActivity Etkinlik Tasarımcısı
description: Bir CompensableActivity etkinliği oluşturmak ve yapılandırmak için İş Akışı Tasarımcısı ' de CompensableActivity etkinlik tasarımcısını nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9612e1b8e808437122df88ad0bbef3a4cce74c0c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955118"
---
# <a name="compensableactivity-activity-designer"></a>CompensableActivity Etkinlik Tasarımcısı

**CompensableActivity** etkinlik Tasarımcısı, etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.Activities.Statements.CompensableActivity> .

## <a name="the-compensableactivity-activity"></a>CompensableActivity etkinliği
 <xref:System.Activities.Statements.CompensableActivity>Başarılı bir şekilde tamamlandıktan sonra onaylanabileceğini veya dengelenebilir bir iş birimi tanımlar.

### <a name="using-the-compensableactivity-activity-designer"></a>CompensableActivity etkinlik tasarımcısını kullanma
 **CompensableActivity** etkinlik Tasarımcısı **araç kutusu** **işlem** kategorisinde bulunabilir. **Araç kutusunu** açmak için iş akışı Tasarımcısı sol tarafında bulunan **araç kutusu** sekmesini seçin. Alternatif olarak, **Görünüm** menüsünden **araç kutusu** ' nu seçin veya **CTRL** + **alt** + **X** tuşlarına basın.

 **CompensableActivity** etkinlik Tasarımcısı **araç kutusu** 'ndan sürüklenip iş akışı Tasarımcısı yüzeyine bırakılabilir. Etkinlik tasarımcısını bir içinde bırakabilirsiniz <xref:System.Activities.Statements.Sequence> . Etkinlik Tasarımcısı ' nın atılması, <xref:System.Activities.Statements.CompensableActivity> varsayılan CompensableActivity ile bir etkinlik oluşturur <xref:System.Activities.Activity.DisplayName%2A> . <xref:System.Activities.Activity.DisplayName%2A> **CompensableActivity** etkinlik Tasarımcısı üstbilgisindeki değeri düzenleyin. Ayrıca, özellik kılavuzunun **DisplayName** kutusunda de düzenlenebilir.

### <a name="the-compensableactivity-properties"></a>CompensableActivity özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.CompensableActivity> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. <xref:System.Activities.Activity.DisplayName%2A>Ve <xref:System.Activities.Activity%601.Result%2A> özelliği özellik kılavuzunda düzenlenebilir, ancak diğer özellikler iş akışı Tasarımcısı yüzeyinde düzenlenmelidir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin isteğe bağlı kolay adı <xref:System.Activities.Statements.CompensableActivity> . Varsayılan değer CompensableActivity 'dir.|
|<xref:System.Activities.Activity%601.Result%2A>|Yanlış|Öğesinin dönüş değerini belirtir <xref:System.Activities.Statements.CompensableActivity> . Bu özellik, özellik kılavuzunda düzenlenmelidir.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|Doğru|Dengeleme, iptal ve onaylama mantığının sağlandığı etkinliği belirtir. Etkinliği eklemek için <xref:System.Activities.Statements.CompensableActivity.Body%2A> , **araç kutusundan** bir etkinliği **CompensableActivity** etkinlik Tasarımcısı ' nın **gövde** kutusuna bırakın. "Etkinliği buraya bırak" ipucu metnini ekleyin.|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|Yanlış|İptal edildiğinde yürütülen etkinliği belirtir. Etkinliği eklemek için, tasarımcısını **araç kutusu** ' ndan, **CompensableActivity** etkinlik Tasarımcısı ' nın **CancellationHandler** kutusuna bırakın. İpucu metni Ekle "etkinliği buraya bırakın".|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|Yanlış|Etkinlik için telafi edildiğinde yürütülecek etkinliği belirtir <xref:System.Activities.Statements.CompensableActivity.Body%2A> . Bu işleyici, etkinlik kullanılarak açık bir şekilde çağrılabilir <xref:System.Activities.Statements.Compensate> .<br /><br /> Etkinliği eklemek için, etkinlik tasarımcısını **araç kutusu** ' ndan **CompensableActivity** etkinlik Tasarımcısı ' nın **CompensationHandler** kutusuna bırakın. İpucu metni Ekle "etkinliği buraya bırakın".|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|Yanlış|Etkinlik onaylandığınızda yürütülecek etkinliği belirtir <xref:System.Activities.Statements.CompensableActivity.Body%2A> . Bu işleyici, etkinlik kullanılarak açık bir şekilde çağrılabilir <xref:System.Activities.Statements.Confirm> .<br /><br /> Etkinliği eklemek için, etkinlik tasarımcısını **araç kutusu** ' ndan **CompensableActivity** etkinlik Tasarımcısı ' nın **ConfirmationHandler** kutusuna bırakın. İpucu metni Ekle "etkinliği buraya bırakın".|

## <a name="see-also"></a>Ayrıca bkz.

- [İşlem](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)
