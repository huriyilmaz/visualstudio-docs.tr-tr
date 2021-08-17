---
title: İş Akışı Tasarımcısı - Etkinlik Tasarımcısını Telafi
description: Telafi etkinlik tasarımcısı hakkında bilgi ve Bir Telafi etkinliği oluşturmak ve yapılandırmak için Telafi etkinlik tasarımcısını nasıl kullanabileceğiniz hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: ca9c66d68913e0791daea6736c7bb5aeeead4df2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122068109"
---
# <a name="compensate-activity-designer"></a>Compensate Etkinlik Tasarımcısı

Etkinliği **oluşturmak** ve yapılandırmak için Telafi etkinliği tasarımcısı <xref:System.Activities.Statements.Compensate> kullanılır.

## <a name="the-compensate-activity"></a>Telafi Etkinliği

Etkinliği, <xref:System.Activities.Statements.Compensate> içinde yer alan bir etkinlik için açıkça <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> <xref:System.Activities.Statements.CompensableActivity> çağırır. Etkinlik <xref:System.Activities.Statements.Compensate> , veya içinde <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> kullanılmazsa, <xref:System.Activities.Statements.CompensableActivity> özelliğini belirtmeniz <xref:System.Activities.Statements.Compensate.Target%2A> gerekir.

<xref:System.Activities.Statements.CompensationToken>tarafından belirtilen, <xref:System.Activities.Statements.Compensate.Target%2A> bir başarıyla tamamlandıktan sonra açıkça onaylamak veya telafi <xref:System.Activities.Statements.CompensableActivity> etmek için bir yol <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity> sağlar.

### <a name="using-the-compensate-activity-designer"></a>Telafi Etkinlik Tasarımcısını Kullanma

Telafi  etkinliği tasarımcısı, Araç Kutusunun **İşlem** kategorisinde **bulunabilir.** Araç **Kutusu'nı** açmak **için, araç** kutusunun sol tarafındaki Araç Kutusu İş Akışı Tasarımcısı. Alternatif olarak Görünüm **menüsünden Araç** Kutusu'nı **seçin** veya **Ctrl** Alt X + **tuşlarına** + **basın.**

**Telafi etkinliği** tasarımcısı Araç Kutusundan  sürüklenip bir içinde olduğu gibi İş Akışı Tasarımcısı yerleştirildikten sonra bu yüzeyde <xref:System.Activities.Statements.Sequence> bırakılır. Etkinlik tasarımcısını bırakarak, Varsayılan <xref:System.Activities.Statements.Compensate> Telafi ile bir etkinlik <xref:System.Activities.Activity.DisplayName%2A> oluşturur. Değer, Telafi etkinlik tasarımcısının üst bilgisinde <xref:System.Activities.Activity.DisplayName%2A> veya özellik kılavuzundaki **DisplayName** kutusunda düzenlenebilir. 

### <a name="the-compensate-properties"></a>Özellikleri Telafi

Aşağıdaki tablo, <xref:System.Activities.Statements.CancellationScope> özellikleri gösterir ve tasarımcıda nasıl kullanıldıklarını açıklar. özelliği <xref:System.Activities.Activity.DisplayName%2A> özellik kılavuzunda veya İş Akışı Tasarımcısı düzenlenebilir. özellik <xref:System.Activities.Statements.Compensate.Target%2A> kılavuzunda özelliğini düzenleyin.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin isteğe bağlı kolay adını <xref:System.Activities.Statements.Compensate> belirtir. Varsayılan değer Telafi'dir.|
|<xref:System.Activities.Statements.Compensate.Target%2A>|Doğru|Bu etkinlik <xref:System.Activities.InArgument%601> için içeren <xref:System.Activities.Statements.CompensationToken> 'i <xref:System.Activities.Statements.Compensate> belirtir.|

## <a name="see-also"></a>Ayrıca bkz.

- [İşlem](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate Etkinlik Tasarımcısı](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)