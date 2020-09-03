---
title: Birlikte çalışma etkinlik Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 994d7776ff7c32f8dd309e667597550637ef2b5a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659034"
---
# <a name="interop-activity-designer"></a>Interop Etkinlik Tasarımcısı
**Birlikte çalışma** etkinlik Tasarımcısı, etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.Activities.Statements.Interop> .

## <a name="the-interop-activity"></a>Birlikte çalışma etkinliği
 <xref:System.Activities.Statements.Interop>Etkinlik, <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> bir iş akışı içinden türetilen türlerin yürütülmesini yönetir.

### <a name="using-the-interop-activity-designer"></a>Birlikte çalışabilirlik etkinlik tasarımcısını kullanma
 **Birlikte çalışma** etkinliği Tasarımcısı **, araç kutusu sekmesine** tıklanarak **erişilen araç kutusu** **geçiş** kategorisinde bulunabilir (alternatif olarak, **Görünüm** menüsünden **araç kutusu** ' nu veya Ctrl + Alt + X ' i seçin.)

 Etkinliği içeren [geçiş](../workflow-designer/migration-activity-designers.md) kategorisi, <xref:System.Activities.Statements.Interop> yalnızca projeniz tam olarak hedefleniyorsa **araç kutusunda** görünür [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)] .

 C# projeleri için, [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] **Çözüm Gezgini** projeye sağ tıklayıp **Özellikler**' i seçerek tam olarak kullanmak için projeyi yeniden hedefleyebilirsiniz. **Uygulama** sekmesinde **hedef çerçevede** **net Framework 4** seçeneğini belirleyin. **Hedef çerçeve değişimi** iletişim kutusunda bu değişikliği onaylamanızı isteyip Istemediğinizi gösteren **Evet** düğmesini seçin.

 VB projeleri için, [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] **Çözüm Gezgini** projeye sağ tıklayıp **Özellikler**' i seçerek tam olarak kullanmak için projeyi yeniden hedefleyebilirsiniz. **Derle** sekmesinde **Gelişmiş derleme seçenekleri** düğmesine tıklayın. **Hedef çerçeve listesinden** **.NET Framework 4** ' ü seçin ve ardından **Tamam**' a tıklayın. **Hedef çerçeve değişimi** iletişim kutusunda bu değişikliği onaylamanızı isteyip Istemediğinizi gösteren **Evet** düğmesine tıklayın.

 **Birlikte çalışabilirlik** etkinlik Tasarımcısı, **araç kutusundan** sürüklenip, ancak [!INCLUDE[wfd2](../includes/wfd2-md.md)] içinde olduğu gibi etkinliklerin genellikle yerleştirildiği yüzeye bırakılabilir <xref:System.Activities.Statements.Sequence> . Bu <xref:System.Activities.Statements.Interop> , birlikte çalışma için varsayılan **DisplayName** olan bir etkinlik oluşturur. , <xref:System.Activities.Activity.DisplayName%2A> **Birlikte çalışma** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

 **Gezinmek Için tıklama düğmesine tıklayın...** **bir .NET türü ve seçme** iletişim kutusunu açmak Için, **birlikte çalışma** Etkinlik tasarımcısında veya özellik kılavuzunda, **ActivityType** kutusundaki metin. Yalnızca iş akışı 3,0 veya iş akışı 3,5 etkinlikleri için türler gösterilir (yani, yalnızca öğesinden türetilmiş türler <xref:System.Workflow.ComponentModel.Activity> ). [!INCLUDE[crabout](../includes/crabout-md.md)] bir tür belirtmek için bu kutuyu kullanarak, [bir .NET türü ve seçme Iletişim kutusu](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md) konusuna bakın.

### <a name="the-interop-properties"></a>Birlikte çalışma özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.Interop> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzunda veya [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyde düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin kolay adı <xref:System.Activities.Statements.Interop> . Varsayılan olarak birlikte çalışabilirlik ' dir. Görünen ad kesinlikle gerekli olmasa da, bir görünen ad kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|Doğru|Etkinliğin içerdiği etkinliğin türünü belirtir <xref:System.Activities.Statements.Interop> . Belirtilen bu tür öğesinden türetilmelidir <xref:System.Workflow.ComponentModel.Activity> .|

## <a name="see-also"></a>Ayrıca Bkz.
 [Geçiş](../workflow-designer/migration-activity-designers.md)