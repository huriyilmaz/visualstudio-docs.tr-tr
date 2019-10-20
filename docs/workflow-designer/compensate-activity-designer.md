---
title: İş Akışı Tasarımcısı-telafi etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 65203663214e6bc82a4a7b20af9caa25bfd98ee4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650648"
---
# <a name="compensate-activity-designer"></a>Compensate Etkinlik Tasarımcısı

**Telafi** etkinliği Tasarımcısı, bir <xref:System.Activities.Statements.Compensate> etkinliği oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-compensate-activity"></a>Telafi etkinliği

@No__t_0 etkinliği, <xref:System.Activities.Statements.CompensableActivity> bulunan bir etkinliğin <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> açıkça çağırır. @No__t_0 etkinliği bir <xref:System.Activities.Statements.CompensableActivity> <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> veya <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> içinde kullanılmıyorsa, <xref:System.Activities.Statements.Compensate.Target%2A> özelliğini belirtmeniz gerekir.

@No__t_1 tarafından belirtilen <xref:System.Activities.Statements.CompensationToken>, <xref:System.Activities.Statements.CompensableActivity> <xref:System.Activities.Statements.CompensableActivity.Body%2A> başarıyla tamamlandığında <xref:System.Activities.Statements.CompensableActivity> açıkça onaylamak veya telafi etmek için bir yol sağlar.

### <a name="using-the-compensate-activity-designer"></a>Telafi etkinliği tasarımcısını kullanma

**Telafi** etkinliği Tasarımcısı **araç kutusunun** **işlem** kategorisinde bulunabilir. **Araç kutusunu**açmak için iş akışı Tasarımcısı sol tarafında bulunan **araç kutusu** sekmesini seçin. Alternatif olarak, **Görünüm** menüsünden **araç kutusu** ' nu seçin veya **CTRL** +**alt** +**X**tuşuna basın.

**Telafi** etkinliği Tasarımcısı **araç kutusundan** sürüklenip, <xref:System.Activities.Statements.Sequence> içinde olduğu gibi etkinliklerin yerleştirildiği iş akışı Tasarımcısı yüzeyine bırakılabilir. Etkinlik Tasarımcısı ' nın atılması, varsayılan telafi <xref:System.Activities.Activity.DisplayName%2A> bir <xref:System.Activities.Statements.Compensate> etkinlik oluşturur. @No__t_0 değeri, **telafi** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-compensate-properties"></a>Telafi özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.CancellationScope> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. @No__t_0 özelliği, özellik kılavuzunda veya İş Akışı Tasarımcısı yüzeyinde düzenlenebilir. Özellik kılavuzundaki <xref:System.Activities.Statements.Compensate.Target%2A> özelliğini düzenleyin.

|Özellik adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|@No__t_0 etkinliğinin isteğe bağlı kolay adını belirtir. Varsayılan olarak telafi 'dir.|
|<xref:System.Activities.Statements.Compensate.Target%2A>|Doğru|Bu <xref:System.Activities.Statements.Compensate> etkinliğinin <xref:System.Activities.Statements.CompensationToken> içeren <xref:System.Activities.InArgument%601> belirtir.|

## <a name="see-also"></a>Ayrıca bkz.

- [İşlem](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate Etkinlik Tasarımcısı](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)