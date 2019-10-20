---
title: İş Akışı Tasarımcısı-TransactionScope etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5d557fb91c52c33022a161bada169d4332bac6b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649829"
---
# <a name="transactionscope-activity-designer"></a>TransactionScope Etkinlik Tasarımcısı

**TransactionScope** etkinlik Tasarımcısı <xref:System.Activities.Statements.TransactionScope> etkinlik oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-transactionscope-activity"></a>TransactionScope etkinliği

@No__t_0 etkinliği içerilen etkinliği tek bir işlemde yürütür. İşlem, <xref:System.Activities.Statements.TransactionScope.Body%2A> etkinliği ve işlemdeki tüm diğer katılımcılar başarıyla tamamlandığında işleme kaydeder.

### <a name="using-the-transactionscope-activity-designer"></a>TransactionScope etkinlik tasarımcısını kullanma

**Araç kutusunun** **işlem** kategorisinde **TransactionScope** etkinlik tasarımcısına erişin. **TransactionScope** etkinlik Tasarımcısı **araç kutusundan** sürüklenip İş Akışı Tasarımcısı yüzeyine, örneğin <xref:System.Activities.Statements.Sequence> içinde olduğu gibi, her yerde bırakılmış olarak bırakılabilir. Bu, TransactionScope 'un varsayılan <xref:System.Activities.Activity.DisplayName%2A> bir <xref:System.Activities.Statements.TransactionScope> etkinlik oluşturur. @No__t_0 değeri, **TransactionScope** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-transactionscope-properties"></a>TransactionScope özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.TransactionScope> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. @No__t_0 ve <xref:System.Activities.Statements.TransactionScope.Body%2A> özellikleri İş Akışı Tasarımcısı yüzeyi üzerinde düzenlenebilir. Ancak diğer özellikler özellik kılavuzunda düzenlenmelidir.

|Özellik adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|@No__t_0 etkinliğinin isteğe bağlı kolay adı. Varsayılan, TransactionScope ' dır. @No__t_0 değeri kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|Doğru|Tek bir işlemde yürütülecek etkinliği belirtir. @No__t_0 etkinliğini eklemek için, **araç kutusundan** bir etkinliği, "ipucu etkinliği buraya bırak" ipucu metni ile **TransactionScope** etkinlik Tasarımcısı ' nın **gövde** kutusuna bırakın.|
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|Doğru|Bu <xref:System.Activities.Statements.TransactionScope> için <xref:System.Transactions.IsolationLevel> belirtir.|
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|İşlemin tamamlanmasının 00:00:00 gerektiği zaman aralığını belirtir (Saat: dakika: saniye). Varsayılan değer 1 dakikadır (00:01:00).|
|[System. Activities. deyimlerini. TransactionScope. AbortInstanceOnTransactionFailure](https://msdn.microsoft.com/library/system.activities.statements.transactionscope.abortinstanceontransactionfailure.aspx)|Doğru|İşlem iptal edildikten sonra iş akışının durdurulmayacağını belirten değeri belirtir.|

## <a name="see-also"></a>Ayrıca bkz.

- [İşlem](../workflow-designer/transaction-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)