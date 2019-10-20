---
title: Telafi etkinlik Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 706cd446e931d6a3a065a3e8abfb58b5a90e9152
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656983"
---
# <a name="compensate-activity-designer"></a>Compensate Etkinlik Tasarımcısı
**Telafi** etkinliği Tasarımcısı, bir <xref:System.Activities.Statements.Compensate> etkinliği oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-compensate-activity"></a>Telafi etkinliği
 @No__t_0 etkinliği, <xref:System.Activities.Statements.CompensableActivity> bulunan bir etkinliğin <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> açıkça çağırır. @No__t_0 etkinliği bir <xref:System.Activities.Statements.CompensableActivity> <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> veya <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> içinde kullanılmıyorsa, <xref:System.Activities.Statements.Compensate.Target%2A> özelliğini belirtmeniz gerekir.

 @No__t_1 tarafından belirtilen <xref:System.Activities.Statements.CompensationToken>, <xref:System.Activities.Statements.CompensableActivity> <xref:System.Activities.Statements.CompensableActivity.Body%2A> başarıyla tamamlandığında <xref:System.Activities.Statements.CompensableActivity> açıkça onaylamak veya telafi etmek için bir yol sağlar.

### <a name="using-the-compensate-activity-designer"></a>Telafi etkinliği tasarımcısını kullanma
 **Telafi** etkinliği tasarımcısı, [!INCLUDE[wfd2](../includes/wfd2-md.md)] sol **tarafındaki araç** **kutusu** sekmesine tıklanarak erişilen **araç kutusu**işlem kategorisinde bulunabilir (alternatif olarak,  **Görünüm** menüsü veya Ctrl + Alt + X.)

 **Telafi** etkinliği Tasarımcısı **araç kutusundan** sürüklenip [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyine, örneğin <xref:System.Activities.Statements.Sequence> içinde olduğu gibi, her yerde bırakılmış olarak bırakılabilir. Bu, varsayılan telafi <xref:System.Activities.Activity.DisplayName%2A> bir <xref:System.Activities.Statements.Compensate> etkinliği oluşturur. @No__t_0 değeri, **telafi** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-compensate-properties"></a>Telafi özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.CancellationScope> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. @No__t_0 özelliği, özellik kılavuzunda veya [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyinde düzenlenebilir, ancak özellik kılavuzunda <xref:System.Activities.Statements.Compensate.Target%2A> özelliği düzenlenmelidir.

|Özellik adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|@No__t_0 etkinliğinin isteğe bağlı kolay adını belirtir. Varsayılan olarak telafi 'dir.|
|<xref:System.Activities.Statements.Compensate.Target%2A>|Doğru|Bu <xref:System.Activities.Statements.Compensate> etkinliğinin <xref:System.Activities.Statements.CompensationToken> içeren <xref:System.Activities.InArgument%601> belirtir.|

## <a name="see-also"></a>Ayrıca Bkz.
 [İşlem](../workflow-designer/transaction-activity-designers.md) [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [telafi etkinlik Tasarımcısı](../workflow-designer/compensate-activity-designer.md) [](../workflow-designer/confirm-activity-designer.md) [TransactionScope](../workflow-designer/transactionscope-activity-designer.md) 'u onaylayın