---
title: İş Akışı Tasarımcısı-CompensableActivity etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ec70c22ae195dc6dd58aa2cfa893cee35fe6ca8
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597106"
---
# <a name="compensableactivity-activity-designer"></a>CompensableActivity Etkinlik Tasarımcısı

**CompensableActivity** etkinlik Tasarımcısı <xref:System.Activities.Statements.CompensableActivity> etkinlik oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-compensableactivity-activity"></a>CompensableActivity etkinliği
 <xref:System.Activities.Statements.CompensableActivity> başarılı bir şekilde tamamlandıktan sonra onaylanabileceğini veya dengelenebilir bir iş birimi tanımlar.

### <a name="using-the-compensableactivity-activity-designer"></a>CompensableActivity etkinlik tasarımcısını kullanma
 **CompensableActivity** etkinlik Tasarımcısı **araç kutusu** **işlem** kategorisinde bulunabilir. **Araç kutusunu**açmak için iş akışı Tasarımcısı sol tarafında bulunan **araç kutusu** sekmesini seçin. Alternatif olarak, **Görünüm** menüsünden **araç kutusu** ' nu seçin veya **CTRL**+**alt**+**X**tuşuna basın.

 **CompensableActivity** etkinlik Tasarımcısı **araç kutusu** 'ndan sürüklenip iş akışı Tasarımcısı yüzeyine bırakılabilir. Etkinlik tasarımcısını bir <xref:System.Activities.Statements.Sequence>içine bırakabilirsiniz. Etkinlik Tasarımcısı ' nın atılması, CompensableActivity 'nin varsayılan <xref:System.Activities.Activity.DisplayName%2A> bir <xref:System.Activities.Statements.CompensableActivity> etkinlik oluşturur. **CompensableActivity** etkinlik tasarımcısı üstbilgisindeki <xref:System.Activities.Activity.DisplayName%2A> değerini düzenleyin. Ayrıca, özellik kılavuzunun **DisplayName** kutusunda de düzenlenebilir.

### <a name="the-compensableactivity-properties"></a>CompensableActivity özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.CompensableActivity> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. <xref:System.Activities.Activity.DisplayName%2A> ve <xref:System.Activities.Activity%601.Result%2A> özelliği özellik kılavuzunda düzenlenebilir, ancak diğer özellikler İş Akışı Tasarımcısı yüzeyinde düzenlenmelidir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.CompensableActivity> etkinliğinin isteğe bağlı kolay adı. Varsayılan değer CompensableActivity 'dir.|
|<xref:System.Activities.Activity%601.Result%2A>|False|<xref:System.Activities.Statements.CompensableActivity>dönüş değerini belirtir. Bu özellik, özellik kılavuzunda düzenlenmelidir.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|Doğru|Dengeleme, iptal ve onaylama mantığının sağlandığı etkinliği belirtir. <xref:System.Activities.Statements.CompensableActivity.Body%2A> etkinliğini eklemek için, **araç** kutusundan bir etkinliği **CompensableActivity** etkinlik Tasarımcısı ' nın **gövde** kutusuna bırakın. "Etkinliği buraya bırak" ipucu metnini ekleyin.|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|İptal edildiğinde yürütülen etkinliği belirtir. Etkinliği eklemek için, tasarımcısını **araç kutusu** ' ndan, **CompensableActivity** etkinlik Tasarımcısı ' nın **CancellationHandler** kutusuna bırakın. İpucu metni Ekle "etkinliği buraya bırakın".|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|<xref:System.Activities.Statements.CompensableActivity.Body%2A> etkinliği için telafi edildiğinde yürütülecek etkinliği belirtir. Bu işleyici, <xref:System.Activities.Statements.Compensate> etkinliği kullanılarak açık bir şekilde çağrılabilir.<br /><br /> Etkinliği eklemek için, etkinlik tasarımcısını **araç kutusu** ' ndan **CompensableActivity** etkinlik Tasarımcısı ' nın **CompensationHandler** kutusuna bırakın. İpucu metni Ekle "etkinliği buraya bırakın".|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|<xref:System.Activities.Statements.CompensableActivity.Body%2A> etkinliğini onaylayarak yürütülecek etkinliği belirtir. Bu işleyici, <xref:System.Activities.Statements.Confirm> etkinliği kullanılarak açık bir şekilde çağrılabilir.<br /><br /> Etkinliği eklemek için, etkinlik tasarımcısını **araç kutusu** ' ndan **CompensableActivity** etkinlik Tasarımcısı ' nın **ConfirmationHandler** kutusuna bırakın. İpucu metni Ekle "etkinliği buraya bırakın".|

## <a name="see-also"></a>Ayrıca bkz.

- [İşlem](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)
