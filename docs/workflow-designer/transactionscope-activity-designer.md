---
title: İş Akışı Tasarımcısı-TransactionScope etkinlik Tasarımcısı
description: TransactionScope etkinliğini oluşturmak ve yapılandırmak için TransactionScope etkinlik tasarımcısını nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 234e6c2d0349cf610d9ba22d53ce59e3768ad64e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838015"
---
# <a name="transactionscope-activity-designer"></a>TransactionScope Etkinlik Tasarımcısı

**TransactionScope** etkinlik Tasarımcısı, etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.Activities.Statements.TransactionScope> .

## <a name="the-transactionscope-activity"></a>TransactionScope etkinliği

<xref:System.Activities.Statements.TransactionScope>Etkinlik, içerilen etkinliği tek bir işlemde yürütür. İşlem, <xref:System.Activities.Statements.TransactionScope.Body%2A> etkinlik ve işlemdeki tüm diğer katılımcılar başarıyla tamamlandığında işleme kaydeder.

### <a name="using-the-transactionscope-activity-designer"></a>TransactionScope etkinlik tasarımcısını kullanma

**Araç kutusunun** **işlem** kategorisinde **TransactionScope** etkinlik tasarımcısına erişin. **TransactionScope** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, içindeki gibi etkinliklerin genellikle yerleştirildiği iş akışı Tasarımcısı yüzeyine bırakılabilir <xref:System.Activities.Statements.Sequence> . Bu <xref:System.Activities.Statements.TransactionScope> , varsayılan bir TransactionScope içeren bir etkinlik oluşturur <xref:System.Activities.Activity.DisplayName%2A> . <xref:System.Activities.Activity.DisplayName%2A>Değer, **TransactionScope** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-transactionscope-properties"></a>TransactionScope özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.TransactionScope> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. <xref:System.Activities.Activity.DisplayName%2A>Ve <xref:System.Activities.Statements.TransactionScope.Body%2A> özellikleri iş akışı Tasarımcısı yüzeyi üzerinde düzenlenebilir. Ancak diğer özellikler özellik kılavuzunda düzenlenmelidir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin isteğe bağlı kolay adı <xref:System.Activities.Statements.TransactionScope> . Varsayılan, TransactionScope ' dır. <xref:System.Activities.Activity.DisplayName%2A>Değer kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|Doğru|Tek bir işlemde yürütülecek etkinliği belirtir. Etkinliği eklemek için <xref:System.Activities.Statements.TransactionScope.Body%2A> , **araç kutusundan** bir etkinliği, metin kutusundan **TransactionScope** etkinlik Tasarımcısı ' nın **gövde** kutusuna bırakın ve ipucu metni "etkinliği buraya bırak" yazın.|
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|Doğru|<xref:System.Transactions.IsolationLevel>Bunun için belirtir <xref:System.Activities.Statements.TransactionScope> .|
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|Yanlış|İşlemin tamamlanmasının 00:00:00 gerektiği zaman aralığını belirtir (Saat: dakika: saniye). Varsayılan değer 1 dakikadır (00:01:00).|
|<xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure*>|Doğru|İşlem iptal edildikten sonra iş akışının durdurulmayacağını belirten değeri belirtir.|

## <a name="see-also"></a>Ayrıca bkz.

- [İşlem](../workflow-designer/transaction-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
