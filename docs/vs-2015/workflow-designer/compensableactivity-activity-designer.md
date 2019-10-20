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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656989"
---
# <a name="compensableactivity-activity-designer"></a>CompensableActivity Etkinlik Tasarımcısı
**CompensableActivity** etkinlik Tasarımcısı <xref:System.Activities.Statements.CompensableActivity> etkinlik oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-compensableactivity-activity"></a>CompensableActivity etkinliği
 @No__t_0 başarılı bir şekilde tamamlandıktan sonra onaylanabileceğini veya dengelenebilir bir iş birimi tanımlar.

### <a name="using-the-compensableactivity-activity-designer"></a>CompensableActivity etkinlik tasarımcısını kullanma
 **CompensableActivity** etkinlik tasarımcısı, [!INCLUDE[wfd2](../includes/wfd2-md.md)] sol tarafındaki araç **kutusu** sekmesine tıklanarak erişilen **araç kutusunun** **Işlem** kategorisinde bulunabilir (alternatif olarak, **araç çubuğu** ' nu seçin). **Görünüm** menüsünden veya Ctrl + Alt + X.)

 **CompensableActivity** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, örneğin <xref:System.Activities.Statements.Sequence> gibi etkinliklerin genellikle yerleştirildiği [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyine bırakılabilir. Bu, CompensableActivity 'nin varsayılan <xref:System.Activities.Activity.DisplayName%2A> bir <xref:System.Activities.Statements.CompensableActivity> etkinliği oluşturur. @No__t_0 değeri, **CompensableActivity** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-compensableactivity-properties"></a>CompensableActivity özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.CompensableActivity> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. @No__t_0 ve <xref:System.Activities.Activity%601.Result%2A> özelliği özellik kılavuzunda düzenlenebilir, ancak diğer özellikler [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyinde düzenlenmelidir.

|Özellik adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|@No__t_0 etkinliğinin isteğe bağlı kolay adı. Varsayılan değer CompensableActivity 'dir.|
|<xref:System.Activities.Activity%601.Result%2A>|False|@No__t_0 dönüş değerini belirtir. Bu özellik, özellik kılavuzunda düzenlenmelidir.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|Doğru|Dengeleme, iptal ve onaylama mantığının sağlandığı etkinliği belirtir. @No__t_0 etkinliğini eklemek için, **araç kutusundan** bir etkinliği bir etkinlik kutusu 'Ndan **CompensableActivity** etkinlik Tasarımcısı ' nın **gövde** kutusuna ekleyin ve ipucu metni "etkinliği buraya bırakın" yazın.|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|İptal durumunda yürütülen etkinliği belirtir. Etkinliği eklemek için, tasarımcı 'yı **araç kutusundan** , **CompensableActivity** etkinlik Tasarımcısı 'ndaki **CancellationHandler** kutusuna, ipucu metni "etkinliği buraya bırak" olarak bırakın.|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|@No__t_0 etkinliği için telafi edildiğinde yürütülecek etkinliği belirtir. Bu işleyici, <xref:System.Activities.Statements.Compensate> etkinliği kullanılarak açık bir şekilde çağrılabilir.<br /><br /> Etkinliği eklemek için, etkinlik tasarımcısını **araç kutusundan** , **CompensableActivity** etkinlik Tasarımcısı 'ndaki **CompensationHandler** kutusuna, Ipucu metni "bırakma etkinliği buraya bırak" olarak bırakın.|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|@No__t_0 etkinliğini onaylayarak yürütülecek etkinliği belirtir. Bu işleyici, <xref:System.Activities.Statements.Confirm> etkinliği kullanılarak açık bir şekilde çağrılabilir.<br /><br /> Etkinliği eklemek için, etkinlik tasarımcısını **araç kutusundan** , **CompensableActivity** etkinlik Tasarımcısı ' nın **ConfirmationHandler** kutusuna, ipucu metni "etkinliği buraya bırak" olarak bırakın.|

## <a name="see-also"></a>Ayrıca Bkz.
 [İşlem](../workflow-designer/transaction-activity-designers.md) [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md) [telafi](../workflow-designer/compensate-activity-designer.md) , [TransactionScope](../workflow-designer/transactionscope-activity-designer.md) 'u [onaylayın](../workflow-designer/confirm-activity-designer.md)