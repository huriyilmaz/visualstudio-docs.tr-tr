---
title: CompensableActivity etkinlik Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e2bc28c4586912d7c253c9629c2af0eefd30e47e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656989"
---
# <a name="compensableactivity-activity-designer"></a>CompensableActivity Etkinlik Tasarımcısı
**CompensableActivity** etkinlik Tasarımcısı, etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.Activities.Statements.CompensableActivity> .

## <a name="the-compensableactivity-activity"></a>CompensableActivity etkinliği
 <xref:System.Activities.Statements.CompensableActivity>Başarılı bir şekilde tamamlandıktan sonra onaylanabileceğini veya dengelenebilir bir iş birimi tanımlar.

### <a name="using-the-compensableactivity-activity-designer"></a>CompensableActivity etkinlik tasarımcısını kullanma
 **CompensableActivity** etkinlik Tasarımcısı, ' ın sol tarafındaki araç **kutusu** sekmesine tıklanarak erişilen **araç kutusunun** **Işlem** kategorisinde bulunabilir [!INCLUDE[wfd2](../includes/wfd2-md.md)] (alternatif olarak, **Görünüm** menüsünden **araç çubuğu** ' nu veya Ctrl + Alt + X ' i seçin.)

 **CompensableActivity** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, ancak [!INCLUDE[wfd2](../includes/wfd2-md.md)] içinde olduğu gibi etkinliklerin genellikle yerleştirildiği yüzeyine bırakılabilir <xref:System.Activities.Statements.Sequence> . Bu <xref:System.Activities.Statements.CompensableActivity> , varsayılan CompensableActivity olan bir etkinlik oluşturur <xref:System.Activities.Activity.DisplayName%2A> . <xref:System.Activities.Activity.DisplayName%2A>Değer, **CompensableActivity** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-compensableactivity-properties"></a>CompensableActivity özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.CompensableActivity> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. <xref:System.Activities.Activity.DisplayName%2A>Ve <xref:System.Activities.Activity%601.Result%2A> özelliği özellik kılavuzunda düzenlenebilir, ancak diğer özellikler yüzeyinde düzenlenmelidir [!INCLUDE[wfd2](../includes/wfd2-md.md)] .

|Özellik Adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin isteğe bağlı kolay adı <xref:System.Activities.Statements.CompensableActivity> . Varsayılan değer CompensableActivity 'dir.|
|<xref:System.Activities.Activity%601.Result%2A>|Yanlış|Öğesinin dönüş değerini belirtir <xref:System.Activities.Statements.CompensableActivity> . Bu özellik, özellik kılavuzunda düzenlenmelidir.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|Doğru|Dengeleme, iptal ve onaylama mantığının sağlandığı etkinliği belirtir. Etkinliği eklemek için <xref:System.Activities.Statements.CompensableActivity.Body%2A> , **araç kutusundan** bir etkinliği bir etkinlik kutusu 'Ndan **CompensableActivity** etkinlik Tasarımcısı ' nın **gövde** kutusuna ekleyin ve ipucu metni "etkinliği buraya bırakın" yazın.|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|Yanlış|İptal durumunda yürütülen etkinliği belirtir. Etkinliği eklemek için, tasarımcı 'yı **araç kutusundan** , **CompensableActivity** etkinlik Tasarımcısı 'ndaki **CancellationHandler** kutusuna, ipucu metni "etkinliği buraya bırak" olarak bırakın.|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|Yanlış|Etkinlik için telafi edildiğinde yürütülecek etkinliği belirtir <xref:System.Activities.Statements.CompensableActivity.Body%2A> . Bu işleyici, etkinlik kullanılarak açık bir şekilde çağrılabilir <xref:System.Activities.Statements.Compensate> .<br /><br /> Etkinliği eklemek için, etkinlik tasarımcısını **araç kutusundan** , **CompensableActivity** etkinlik Tasarımcısı 'ndaki **CompensationHandler** kutusuna, Ipucu metni "bırakma etkinliği buraya bırak" olarak bırakın.|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|Yanlış|Etkinlik onaylandığınızda yürütülecek etkinliği belirtir <xref:System.Activities.Statements.CompensableActivity.Body%2A> . Bu işleyici, etkinlik kullanılarak açık bir şekilde çağrılabilir <xref:System.Activities.Statements.Confirm> .<br /><br /> Etkinliği eklemek için, etkinlik tasarımcısını **araç kutusundan** , **CompensableActivity** etkinlik Tasarımcısı ' nın **ConfirmationHandler** kutusuna, ipucu metni "etkinliği buraya bırak" olarak bırakın.|

## <a name="see-also"></a>Ayrıca Bkz.
 [İşlem](../workflow-designer/transaction-activity-designers.md) [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md) [telafi](../workflow-designer/compensate-activity-designer.md) , [TransactionScope](../workflow-designer/transactionscope-activity-designer.md) 'u [onaylayın](../workflow-designer/confirm-activity-designer.md)