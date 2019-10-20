---
title: TransactionScope etkinlik Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b5a1d38ea37896cedcd2166c42f37ce037a1c4cd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670182"
---
# <a name="transactionscope-activity-designer"></a>TransactionScope Etkinlik Tasarımcısı
**TransactionScope** etkinlik Tasarımcısı <xref:System.Activities.Statements.TransactionScope> etkinlik oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-transactionscope-activity"></a>TransactionScope etkinliği
 @No__t_0 etkinliği içerilen etkinliği tek bir işlemde yürütür. İşlem, <xref:System.Activities.Statements.TransactionScope.Body%2A> etkinliği ve işlemdeki tüm diğer katılımcılar başarıyla tamamlandığında işleme kaydeder.

### <a name="using-the-transactionscope-activity-designer"></a>TransactionScope etkinlik tasarımcısını kullanma
 **TransactionScope** etkinlik tasarımcısı, [!INCLUDE[wfd2](../includes/wfd2-md.md)] araç **kutusu** sekmesine tıklanarak erişilen **araç kutusu** **Işlem** kategorisinde bulunabilir (alternatif olarak, **görünümden** **araç çubuğu** ' nu seçin). menü veya CTRL + ALT + X.)

 **TransactionScope** etkinlik Tasarımcısı **araç kutusundan** sürüklenip [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyine, örneğin <xref:System.Activities.Statements.Sequence> içinde olduğu gibi, her yerde bırakılmış olarak bırakılabilir. Bu, TransactionScope 'un varsayılan <xref:System.Activities.Activity.DisplayName%2A> bir <xref:System.Activities.Statements.TransactionScope> etkinlik oluşturur. @No__t_0 değeri, **TransactionScope** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-transactionscope-properties"></a>TransactionScope özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.TransactionScope> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. @No__t_0 ve <xref:System.Activities.Statements.TransactionScope.Body%2A> özellikleri [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyi üzerinde düzenlenebilir. Ancak diğer özellikler özellik kılavuzunda düzenlenmelidir.

|Özellik adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|@No__t_0 etkinliğinin isteğe bağlı kolay adı. Varsayılan, TransactionScope ' dır. @No__t_0 değeri kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|Doğru|Tek bir işlemde yürütülecek etkinliği belirtir. @No__t_0 etkinliğini eklemek için, **araç kutusundan** bir etkinliği, "ipucu etkinliği buraya bırak" ipucu metni ile **TransactionScope** etkinlik Tasarımcısı ' nın **gövde** kutusuna bırakın.|
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|Doğru|Bu <xref:System.Activities.Statements.TransactionScope> için <xref:System.Transactions.IsolationLevel> belirtir.|
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|İşlemin tamamlanmasının 00:00:00 gerektiği zaman aralığını belirtir (Saat: dakika: saniye). Varsayılan değer 1 dakikadır (00:01:00).|
|<xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure?qualifyHint=False&autoUpgrade=True>|Doğru|İşlem iptal edildikten sonra iş akışının durdurulmayacağını belirten değeri belirtir.|

## <a name="see-also"></a>Ayrıca Bkz.
 [İşlem](../workflow-designer/transaction-activity-designers.md) [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md) [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [telafi](../workflow-designer/compensate-activity-designer.md) [onaylama](../workflow-designer/confirm-activity-designer.md)