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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659176"
---
# <a name="cancellationscope-activity-designer"></a>CancellationScope Etkinlik Tasarımcısı
**CancellationScope** etkinlik Tasarımcısı <xref:System.Activities.Statements.CancellationScope> etkinlik oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-cancellationscope-activity"></a>CancellationScope etkinliği
 @No__t_0 etkinliği, bu etkinlik için yürütme ve iptal mantığı için bir etkinlik belirtmenize olanak tanır.

### <a name="using-the-cancellationscope-activity-designer"></a>CancellationScope Etkinlik tasarımcısını kullanma
 **CancellationScope** etkinlik tasarımcısı, [!INCLUDE[wfd2](../includes/wfd2-md.md)] araç **kutusu** sekmesine tıklanarak erişilen **araç kutusunun** **Işlem** kategorisinde bulunabilir (alternatif olarak, görünümden **araç çubuğu** ' nu seçin).menü veya Ctrl + Alt + X.)

 **CancellationScope** etkinlik Tasarımcısı **araç kutusundan** sürüklenip [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyine, örneğin <xref:System.Activities.Statements.Sequence> içinde olduğu gibi, her yerde bırakılmış olarak bırakılabilir. Bu, varsayılan <xref:System.Activities.Activity.DisplayName%2A> bir <xref:System.Activities.Statements.CancellationScope> etkinlik oluşturur. @No__t_0 değeri, **CancellationScope** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-cancellationscope-properties"></a>CancellationScope özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.CancellationScope> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. @No__t_0 özelliği özellik kılavuzunda düzenlenebilir, ancak diğer özellikler [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyinde düzenlenmelidir.

|Özellik adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|@No__t_0 etkinliğinin isteğe bağlı kolay adı. Varsayılan değer CancellationScope ' dir. @No__t_0 değeri kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|Doğru|İptal mantığının sağlandığı etkinliği belirtir. @No__t_0 etkinliğini eklemek için, **araç kutusundan** bir etkinliği **CancellationScope** etkinlik Tasarımcısı ' nın "Ipucu" etkinliği buraya bırak "ipucu metnini içeren **gövde** kutusuna bırakın.|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|Doğru|İptal durumunda yürütülen etkinliği belirtir. @No__t_0 etkinliğini eklemek için, **araç kutusundan** bir etkinliği **CancellationScope** Activity Designer 'daki **CancellationHandler** kutusuna bir etkinlik bırakın ve ipucu "etkinliği buraya bırak" ipucu metnini ekleyin.|

## <a name="see-also"></a>Ayrıca Bkz.
 [İşlem](../workflow-designer/transaction-activity-designers.md) [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [telafi](../workflow-designer/compensate-activity-designer.md) , [TransactionScope](../workflow-designer/transactionscope-activity-designer.md) 'u [onaylayın](../workflow-designer/confirm-activity-designer.md)