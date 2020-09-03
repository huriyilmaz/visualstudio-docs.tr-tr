---
title: CancellationScope Etkinlik Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fa41d63fa4f67037a8e98e72abc3e338ad894f70
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659176"
---
# <a name="cancellationscope-activity-designer"></a>CancellationScope Etkinlik Tasarımcısı
**CancellationScope** etkinlik Tasarımcısı bir etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.Activities.Statements.CancellationScope> .

## <a name="the-cancellationscope-activity"></a>CancellationScope etkinliği
 <xref:System.Activities.Statements.CancellationScope>Etkinlik, bu etkinlik için yürütme ve iptal mantığı için bir etkinlik belirtmenize olanak tanır.

### <a name="using-the-cancellationscope-activity-designer"></a>CancellationScope Etkinlik tasarımcısını kullanma
 **CancellationScope** etkinlik Tasarımcısı, araç **kutusu** sekmesine tıklanarak **Transaction** erişilen (alternatif olarak **Toolbox** [!INCLUDE[wfd2](../includes/wfd2-md.md)] , **Görünüm** menüsünden **araç çubuğu** ' nu veya Ctrl + Alt + X ' i seçin.) araç kutusu işlem kategorisinde bulunabilir.

 **CancellationScope** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, [!INCLUDE[wfd2](../includes/wfd2-md.md)] Örneğin içinde olduğu gibi etkinliklerin genellikle yerleştirildiği yüzeyine bırakılabilir <xref:System.Activities.Statements.Sequence> . Bu <xref:System.Activities.Statements.CancellationScope> , varsayılan CancellationScope bir etkinlik oluşturur <xref:System.Activities.Activity.DisplayName%2A> . <xref:System.Activities.Activity.DisplayName%2A>Değer, **CancellationScope** etkinlik Tasarımcısı üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-cancellationscope-properties"></a>CancellationScope özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.CancellationScope> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. <xref:System.Activities.Activity.DisplayName%2A>Özellik, özellik kılavuzunda düzenlenebilir, ancak diğer özellikler yüzeyinde düzenlenmelidir [!INCLUDE[wfd2](../includes/wfd2-md.md)] .

|Özellik Adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin isteğe bağlı kolay adı <xref:System.Activities.Statements.CancellationScope> . Varsayılan değer CancellationScope ' dir. <xref:System.Activities.Activity.DisplayName%2A>Değer kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|Doğru|İptal mantığının sağlandığı etkinliği belirtir. Etkinliği eklemek için <xref:System.Activities.Statements.CancellationScope.Body%2A> , **araç kutusundan** bir etkinliği **CancellationScope** etkinlik Tasarımcısı ' nın "ipucu" etkinliği buraya bırak "ipucu metnini içeren **gövde** kutusuna bırakın.|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|Doğru|İptal durumunda yürütülen etkinliği belirtir. Etkinliği eklemek için <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> , **araç kutusundan** bir etkinliği, **CancellationScope** Etkinlik tasarımcısında bulunan **CancellationHandler** kutusuna bir etkinlik bırakın ve ipucu "etkinliği buraya bırak" ipucu metnini ekleyin.|

## <a name="see-also"></a>Ayrıca Bkz.
 [İşlem](../workflow-designer/transaction-activity-designers.md) [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [telafi](../workflow-designer/compensate-activity-designer.md) , [TransactionScope](../workflow-designer/transactionscope-activity-designer.md) 'u [onaylayın](../workflow-designer/confirm-activity-designer.md)