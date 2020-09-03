---
title: İş Akışı Tasarımcısı-etkinlik tasarımcısını Onayla
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Confirm.UI
ms.assetid: c753b67b-b0e7-462a-bb4e-ba8db04a078d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: abd7fedd958072baf23b456f9897ab67c864991d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86876144"
---
# <a name="confirm-activity-designer"></a>Confirm Etkinlik Tasarımcısı

Etkinlik oluşturmak ve yapılandırmak için **onaylama** etkinliği Tasarımcısı kullanılır <xref:System.Activities.Statements.Confirm> .

## <a name="the-confirm-activity"></a>Onayla etkinliği
 <xref:System.Activities.Statements.Confirm>Etkinlik, <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> içinde bulunan bir etkinlik için açıkça öğesini çağırır <xref:System.Activities.Statements.CompensableActivity> . Etkinlik, <xref:System.Activities.Statements.Confirm> veya bir içinde kullanılmıyorsa, <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> <xref:System.Activities.Statements.CompensableActivity> özelliğini belirtmeniz gerekir <xref:System.Activities.Statements.Confirm.Target%2A> .

 <xref:System.Activities.Statements.CompensationToken>Tarafından belirtilen, <xref:System.Activities.Statements.Compensate.Target%2A> başarıyla tamamlandıktan sonra açıkça onaylamak veya telafi etmek için bir yol sağlar <xref:System.Activities.Statements.CompensableActivity> <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity> .

### <a name="using-the-confirm-activity-designer"></a>Onaylama etkinliği tasarımcısını kullanma
 **Onaylama** etkinliği tasarımcısı, iş akışı Tasarımcısı sol tarafındaki **araç kutusu** sekmesine tıklanarak erişilen **araç kutusu** **işlem** kategorisinde bulunabilir. Alternatif olarak, **Görünüm** menüsünden **araç kutusu** ' nu seçin veya **CTRL** + **alt** + **X**tuşlarına basın.

 **Onaylama** etkinliği Tasarımcısı **araç kutusundan** sürüklenip, örneğin içinde olduğu gibi etkinliklerin genellikle yerleştirildiği iş akışı Tasarımcısı yüzeyine bırakılabilir <xref:System.Activities.Statements.Sequence> . Bu <xref:System.Activities.Statements.Confirm> , varsayılan Onayla olan bir etkinlik oluşturur <xref:System.Activities.Activity.DisplayName%2A> . <xref:System.Activities.Activity.DisplayName%2A>Değer, **Onayla** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-confirm-properties"></a>Özellikleri Onayla
 Aşağıdaki tabloda <xref:System.Activities.Statements.Confirm> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Özellik, özellik <xref:System.Activities.Activity.DisplayName%2A> kılavuzunda veya iş akışı Tasarımcısı yüzeyinde düzenlenebilir ancak özellik, özellik <xref:System.Activities.Statements.Confirm.Target%2A> kılavuzunda düzenlenmelidir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin isteğe bağlı kolay adını belirtir <xref:System.Activities.Statements.CancellationScope> . Varsayılan değer onaylanır.|
|<xref:System.Activities.Statements.Confirm.Target%2A>|Doğru|<xref:System.Activities.InArgument%601> <xref:System.Activities.Statements.CompensationToken> Bu etkinlik için öğesini içeren öğesini belirtir <xref:System.Activities.Statements.Confirm> .|

## <a name="see-also"></a>Ayrıca bkz.

- [İşlem](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)