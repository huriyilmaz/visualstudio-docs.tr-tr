---
title: İş Akışı Tasarımcısı - TransactionScope Etkinlik Tasarımcısı
description: TransactionScope etkinliği oluşturmak ve yapılandırmak için TransactionScope etkinlik tasarımcısını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: d3d84514690c4f2a00caea3b88946ffbd4da7cbc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122114517"
---
# <a name="transactionscope-activity-designer"></a>TransactionScope Etkinlik Tasarımcısı

TransactionScope **etkinlik** tasarımcısı, etkinlik oluşturmak ve yapılandırmak için <xref:System.Activities.Statements.TransactionScope> kullanılır.

## <a name="the-transactionscope-activity"></a>TransactionScope Etkinliği

Etkinlik, <xref:System.Activities.Statements.TransactionScope> içerdiği etkinliği tek bir işlemde yürütür. Etkinlik ve işlemde yer <xref:System.Activities.Statements.TransactionScope.Body%2A> alan diğer tüm katılımcılar başarıyla tamamlandığında işlem tamamlanır.

### <a name="using-the-transactionscope-activity-designer"></a>TransactionScope Etkinlik Tasarımcısını Kullanma

Araç Kutusunun transaction kategorisinde **TransactionScope** **etkinlik** tasarımcısına **erişin.** **TransactionScope** etkinlik tasarımcısı, Araç Kutusundan sürüklenip bir içinde olduğu gibi İş Akışı Tasarımcısı yerleştirildikten sonra bu alan yüzeyine  <xref:System.Activities.Statements.Sequence> bırakılır. Bu, <xref:System.Activities.Statements.TransactionScope> varsayılan TransactionScope değerine sahip <xref:System.Activities.Activity.DisplayName%2A> bir etkinlik oluşturur. Değer <xref:System.Activities.Activity.DisplayName%2A> **TransactionScope** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzundaki **DisplayName** kutusunda düzenlenebilir.

### <a name="the-transactionscope-properties"></a>TransactionScope Özellikleri

Aşağıdaki tablo, <xref:System.Activities.Statements.TransactionScope> özellikleri gösterir ve tasarımcıda nasıl kullanıldıklarını açıklar. ve <xref:System.Activities.Activity.DisplayName%2A> <xref:System.Activities.Statements.TransactionScope.Body%2A> özellikleri, İş Akışı Tasarımcısı düzenlenebilir. Ancak diğer özellikler özellik kılavuzunda düzenlenemez.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin isteğe bağlı kolay <xref:System.Activities.Statements.TransactionScope> adı. Varsayılan değer TransactionScope'tur. Değer <xref:System.Activities.Activity.DisplayName%2A> kesinlikle gerekli değildir ancak bir değer kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|Doğru|Tek bir işlemde yürütülecek etkinliği belirtir. Etkinliği eklemek <xref:System.Activities.Statements.TransactionScope.Body%2A> için Araç Kutusundan  **TransactionScope**  etkinlik tasarımcısında "Etkinliği buraya bırak" ipucu metniyle Gövde kutusuna bir etkinlik bırakın.|
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|Doğru|Bunun için <xref:System.Transactions.IsolationLevel> <xref:System.Activities.Statements.TransactionScope> belirtir.|
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|Yanlış|İşlemin tamamlanması gereken zaman aralığını (saat:dakika:saniye olarak gösteren 00:00:00 olarak biçimlendirildi) belirtir. Varsayılan değer 1 dakikadır (00:01:00).|
|<xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure*>|Doğru|İşlem durdurulsa iş akışının durdurulacak olup olmadığını belirten değeri belirtir.|

## <a name="see-also"></a>Ayrıca bkz.

- [İşlem](../workflow-designer/transaction-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
