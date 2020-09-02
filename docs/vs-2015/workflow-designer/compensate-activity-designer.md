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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656983"
---
# <a name="compensate-activity-designer"></a>Compensate Etkinlik Tasarımcısı
**Telafi** etkinliği Tasarımcısı, etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.Activities.Statements.Compensate> .

## <a name="the-compensate-activity"></a>Telafi etkinliği
 <xref:System.Activities.Statements.Compensate>Etkinlik, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> içinde bulunan bir etkinlik için açıkça öğesini çağırır <xref:System.Activities.Statements.CompensableActivity> . Etkinlik, <xref:System.Activities.Statements.Compensate> veya bir içinde kullanılmıyorsa, <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> <xref:System.Activities.Statements.CompensableActivity> özelliğini belirtmeniz gerekir <xref:System.Activities.Statements.Compensate.Target%2A> .

 <xref:System.Activities.Statements.CompensationToken>Tarafından belirtilen, <xref:System.Activities.Statements.Compensate.Target%2A> başarıyla tamamlandıktan sonra açıkça onaylamak veya telafi etmek için bir yol sağlar <xref:System.Activities.Statements.CompensableActivity> <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity> .

### <a name="using-the-compensate-activity-designer"></a>Telafi etkinliği tasarımcısını kullanma
 **Telafi** etkinliği Tasarımcısı, **araç kutusunun**(alternatif olarak **Transaction** **Toolbox** [!INCLUDE[wfd2](../includes/wfd2-md.md)] , **Görünüm** menüsünden **araç çubuğu** ' nu, ya da Ctrl + Alt + X ' i seçin.) araç kutusu sekmesine tıklanarak erişilen, araç kutusu işlem kategorisinde bulunabilir.

 **Telafi** etkinliği Tasarımcısı **araç kutusundan** sürüklenip, [!INCLUDE[wfd2](../includes/wfd2-md.md)] Örneğin içinde olduğu gibi etkinliklerin genellikle yerleştirildiği yüzeyine bırakılabilir <xref:System.Activities.Statements.Sequence> . Bu <xref:System.Activities.Statements.Compensate> , varsayılan telafi olan bir etkinlik oluşturur <xref:System.Activities.Activity.DisplayName%2A> . <xref:System.Activities.Activity.DisplayName%2A>Değer, **telafi** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-compensate-properties"></a>Telafi özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.CancellationScope> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Özellik, özellik <xref:System.Activities.Activity.DisplayName%2A> kılavuzunda veya [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyinde düzenlenebilir ancak özellik, özellik <xref:System.Activities.Statements.Compensate.Target%2A> kılavuzunda düzenlenmelidir.

|Özellik Adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin isteğe bağlı kolay adını belirtir <xref:System.Activities.Statements.Compensate> . Varsayılan olarak telafi 'dir.|
|<xref:System.Activities.Statements.Compensate.Target%2A>|Doğru|<xref:System.Activities.InArgument%601> <xref:System.Activities.Statements.CompensationToken> Bu etkinlik için öğesini içeren öğesini belirtir <xref:System.Activities.Statements.Compensate> .|

## <a name="see-also"></a>Ayrıca Bkz.
 [İşlem](../workflow-designer/transaction-activity-designers.md) [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [telafi etkinlik Tasarımcısı](../workflow-designer/compensate-activity-designer.md) [Confirm](../workflow-designer/confirm-activity-designer.md) [TransactionScope](../workflow-designer/transactionscope-activity-designer.md) 'u onaylayın