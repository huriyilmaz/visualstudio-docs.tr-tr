---
title: Etkinlik tasarımcısını onaylama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Confirm.UI
ms.assetid: c753b67b-b0e7-462a-bb4e-ba8db04a078d
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b3835c6cb537e7ac74862ac4a6794dd7b0bd5003
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656973"
---
# <a name="confirm-activity-designer"></a>Confirm Etkinlik Tasarımcısı
Bir <xref:System.Activities.Statements.Confirm> etkinliği oluşturmak ve yapılandırmak için **Onayla** etkinliği Tasarımcısı kullanılır.

## <a name="the-confirm-activity"></a>Onayla etkinliği
 @No__t_0 etkinliği, <xref:System.Activities.Statements.CompensableActivity> bulunan bir etkinliğin <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> açıkça çağırır. @No__t_0 etkinliği bir <xref:System.Activities.Statements.CompensableActivity> <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> veya <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> içinde kullanılmıyorsa, <xref:System.Activities.Statements.Confirm.Target%2A> özelliğini belirtmeniz gerekir.

 @No__t_1 tarafından belirtilen <xref:System.Activities.Statements.CompensationToken>, <xref:System.Activities.Statements.CompensableActivity> <xref:System.Activities.Statements.CompensableActivity.Body%2A> başarıyla tamamlandığında <xref:System.Activities.Statements.CompensableActivity> açıkça onaylamak veya telafi etmek için bir yol sağlar.

### <a name="using-the-confirm-activity-designer"></a>Onaylama etkinliği tasarımcısını kullanma
 **Onaylama** etkinliği tasarımcısı, [!INCLUDE[wfd2](../includes/wfd2-md.md)] sol tarafındaki araç **kutusu** sekmesine tıklanarak erişilen **araç kutusu** **Işlem** kategorisinde bulunabilir (alternatif olarak, görünümden **araç çubuğu** ' nu seçin).menü veya Ctrl + Alt + X.)

 **Onaylama** etkinliği Tasarımcısı **araç kutusundan** sürüklenip [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyine, örneğin <xref:System.Activities.Statements.Sequence> içinde olduğu gibi, her yerde bırakılmış olarak bırakılabilir. Bu, varsayılan olarak Onayla <xref:System.Activities.Activity.DisplayName%2A> <xref:System.Activities.Statements.Confirm> bir etkinlik oluşturur. @No__t_0 değeri, **Onayla** etkinliğinin üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-confirm-properties"></a>Özellikleri Onayla
 Aşağıdaki tabloda <xref:System.Activities.Statements.Confirm> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. @No__t_0 özelliği, özellik kılavuzunda veya [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyinde düzenlenebilir, ancak özellik kılavuzunda <xref:System.Activities.Statements.Confirm.Target%2A> özelliği düzenlenmelidir.

|Özellik adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|@No__t_0 etkinliğinin isteğe bağlı kolay adını belirtir. Varsayılan değer onaylanır.|
|<xref:System.Activities.Statements.Confirm.Target%2A>|Doğru|Bu <xref:System.Activities.Statements.Confirm> etkinliğinin <xref:System.Activities.Statements.CompensationToken> içeren <xref:System.Activities.InArgument%601> belirtir.|

## <a name="see-also"></a>Ayrıca Bkz.
 [İşlem](../workflow-designer/transaction-activity-designers.md) [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md) [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [telafi](../workflow-designer/compensate-activity-designer.md) [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)