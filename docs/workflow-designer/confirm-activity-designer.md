---
title: İş Akışı Tasarımcısı - Etkinlik Tasarımcısını Onayla
description: Etkinlik tasarımcısını onayla ve bu tasarımcıyı kullanarak Bir Onayla etkinliği oluşturma ve yapılandırma hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Confirm.UI
ms.assetid: c753b67b-b0e7-462a-bb4e-ba8db04a078d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 017a89d2e68e3d466f7625c8dbb2312d450f888c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122045885"
---
# <a name="confirm-activity-designer"></a>Confirm Etkinlik Tasarımcısı

Etkinlik **oluşturmak** ve yapılandırmak için Etkinlik tasarımcısını onayla <xref:System.Activities.Statements.Confirm> kullanılır.

## <a name="the-confirm-activity"></a>Onayla Etkinliği
 Etkinliği, <xref:System.Activities.Statements.Confirm> içinde yer alan bir etkinlik için açıkça <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> <xref:System.Activities.Statements.CompensableActivity> çağırır. Etkinlik <xref:System.Activities.Statements.Confirm> , veya içinde <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> kullanılmazsa, <xref:System.Activities.Statements.CompensableActivity> özelliğini belirtmeniz <xref:System.Activities.Statements.Confirm.Target%2A> gerekir.

 <xref:System.Activities.Statements.CompensationToken>tarafından belirtilen, <xref:System.Activities.Statements.Compensate.Target%2A> bir başarıyla tamamlandıktan sonra açıkça onaylamak veya telafi <xref:System.Activities.Statements.CompensableActivity> etmek için bir yol <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity> sağlar.

### <a name="using-the-confirm-activity-designer"></a>Etkinlik Tasarımcısını Onayla'nın kullanımı
 Etkinlik **tasarımcısını** onayla,  araç kutusunun sol tarafındaki Araç Kutusu sekmesine tıklayarak erişilen Araç Kutusunun İşlem kategorisinde İş Akışı Tasarımcısı.  Alternatif olarak Görünüm **menüsünden Araç** Kutusu'nı **seçin** veya **Ctrl** Alt X + **tuşlarına** + **basın.**

 **Onayla** etkinlik tasarımcısı Araç Kutusundan sürüklenip bir içinde olduğu gibi İş Akışı Tasarımcısı yerleştirilmelerinden sonra etkinlik yüzeyine  <xref:System.Activities.Statements.Sequence> bırakılır. Bu, varsayılan <xref:System.Activities.Statements.Confirm> Onayla olan bir <xref:System.Activities.Activity.DisplayName%2A> etkinlik oluşturur. Değer, Confirm etkinlik tasarımcısının üst bilgisinde <xref:System.Activities.Activity.DisplayName%2A> veya özellik kılavuzundaki **DisplayName** kutusunda düzenlenebilir. 

### <a name="the-confirm-properties"></a>Özellikleri Onayla
 Aşağıdaki tablo, <xref:System.Activities.Statements.Confirm> özellikleri gösterir ve tasarımcıda nasıl kullanıldıklarını açıklar. özelliği özellik kılavuzunda veya İş Akışı Tasarımcısı <xref:System.Activities.Activity.DisplayName%2A> düzenlenebilir, ancak <xref:System.Activities.Statements.Confirm.Target%2A> özelliğin özellik kılavuzunda düzenlemesi gerekir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin isteğe bağlı kolay adını <xref:System.Activities.Statements.CancellationScope> belirtir. Varsayılan değer Onayla'dır.|
|<xref:System.Activities.Statements.Confirm.Target%2A>|Doğru|Bu etkinlik <xref:System.Activities.InArgument%601> için içeren <xref:System.Activities.Statements.CompensationToken> 'i <xref:System.Activities.Statements.Confirm> belirtir.|

## <a name="see-also"></a>Ayrıca bkz.

- [İşlem](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)