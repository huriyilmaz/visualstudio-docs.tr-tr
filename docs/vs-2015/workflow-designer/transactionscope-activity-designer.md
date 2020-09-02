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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670182"
---
# <a name="transactionscope-activity-designer"></a>TransactionScope Etkinlik Tasarımcısı
**TransactionScope** etkinlik Tasarımcısı, etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.Activities.Statements.TransactionScope> .

## <a name="the-transactionscope-activity"></a>TransactionScope etkinliği
 <xref:System.Activities.Statements.TransactionScope>Etkinlik, içerilen etkinliği tek bir işlemde yürütür. İşlem, <xref:System.Activities.Statements.TransactionScope.Body%2A> etkinlik ve işlemdeki tüm diğer katılımcılar başarıyla tamamlandığında işleme kaydeder.

### <a name="using-the-transactionscope-activity-designer"></a>TransactionScope etkinlik tasarımcısını kullanma
 **TransactionScope** etkinlik **Tasarımcısı araç kutusu sekmesine** tıklanarak erişilen **Toolbox**'ın **Işlem** kategorisinde bulunabilir [!INCLUDE[wfd2](../includes/wfd2-md.md)] (alternatif olarak, **Görünüm** menüsünden **araç çubuğu** ' nu veya Ctrl + Alt + X ' i seçin.)

 **TransactionScope** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, [!INCLUDE[wfd2](../includes/wfd2-md.md)] Örneğin içinde olduğu gibi etkinliklerin genellikle yerleştirildiği yüzeyine bırakılabilir <xref:System.Activities.Statements.Sequence> . Bu <xref:System.Activities.Statements.TransactionScope> , varsayılan bir TransactionScope içeren bir etkinlik oluşturur <xref:System.Activities.Activity.DisplayName%2A> . <xref:System.Activities.Activity.DisplayName%2A>Değer, **TransactionScope** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-transactionscope-properties"></a>TransactionScope özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.TransactionScope> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. <xref:System.Activities.Activity.DisplayName%2A>Ve <xref:System.Activities.Statements.TransactionScope.Body%2A> özellikleri yüzey üzerinde düzenlenebilir [!INCLUDE[wfd2](../includes/wfd2-md.md)] . Ancak diğer özellikler özellik kılavuzunda düzenlenmelidir.

|Özellik Adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin isteğe bağlı kolay adı <xref:System.Activities.Statements.TransactionScope> . Varsayılan, TransactionScope ' dır. <xref:System.Activities.Activity.DisplayName%2A>Değer kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|Doğru|Tek bir işlemde yürütülecek etkinliği belirtir. Etkinliği eklemek için <xref:System.Activities.Statements.TransactionScope.Body%2A> , **araç kutusundan** bir etkinliği, metin kutusundan **TransactionScope** etkinlik Tasarımcısı ' nın **gövde** kutusuna bırakın ve ipucu metni "etkinliği buraya bırak" yazın.|
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|Doğru|<xref:System.Transactions.IsolationLevel>Bunun için belirtir <xref:System.Activities.Statements.TransactionScope> .|
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|Yanlış|İşlemin tamamlanmasının 00:00:00 gerektiği zaman aralığını belirtir (Saat: dakika: saniye). Varsayılan değer 1 dakikadır (00:01:00).|
|<xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure?qualifyHint=False&autoUpgrade=True>|Doğru|İşlem iptal edildikten sonra iş akışının durdurulmayacağını belirten değeri belirtir.|

## <a name="see-also"></a>Ayrıca Bkz.
 [İşlem](../workflow-designer/transaction-activity-designers.md) [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md) [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [telafi](../workflow-designer/compensate-activity-designer.md) [onaylama](../workflow-designer/confirm-activity-designer.md)