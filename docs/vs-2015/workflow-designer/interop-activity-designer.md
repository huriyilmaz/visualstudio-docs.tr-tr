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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659034"
---
# <a name="interop-activity-designer"></a>Interop Etkinlik Tasarımcısı
**Birlikte çalışabilirlik** etkinlik Tasarımcısı, bir <xref:System.Activities.Statements.Interop> etkinliği oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-interop-activity"></a>Birlikte çalışma etkinliği
 @No__t_0 etkinliği, bir iş akışı içinde <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> türetilen türlerin yürütülmesini yönetir.

### <a name="using-the-interop-activity-designer"></a>Birlikte çalışabilirlik etkinlik tasarımcısını kullanma
 **Birlikte çalışma** etkinliği Tasarımcısı **, araç kutusu sekmesine** tıklanarak **erişilen araç kutusu** **geçiş** kategorisinde bulunabilir (alternatif olarak, **Görünüm** menüsünden **araç kutusu** ' nu veya Ctrl + Alt + X ' i seçin.)

 @No__t_1 etkinliğini içeren [geçiş](../workflow-designer/migration-activity-designers.md) kategorisi, yalnızca projeniz tam [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)] hedefliyorsanız **araç kutusunda** görünür.

 Projeler C# için, **Çözüm Gezgini** projeye sağ tıklayıp **özellikler**' i seçerek tam [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] kullanmak için projeyi yeniden hedefleyebilirsiniz. **Uygulama** sekmesinde **hedef çerçevede** **net Framework 4** seçeneğini belirleyin. **Hedef çerçeve değişimi** iletişim kutusunda bu değişikliği onaylamanızı isteyip Istemediğinizi gösteren **Evet** düğmesini seçin.

 VB projeleri için, **Çözüm Gezgini** projeye sağ tıklayıp **Özellikler**' i seçerek tam [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] kullanmak için projeyi yeniden hedefleyebilirsiniz. **Derle** sekmesinde **Gelişmiş derleme seçenekleri** düğmesine tıklayın. **Hedef çerçeve listesinden** **.NET Framework 4** ' ü seçin ve ardından **Tamam**' a tıklayın. **Hedef çerçeve değişimi** iletişim kutusunda bu değişikliği onaylamanızı isteyip Istemediğinizi gösteren **Evet** düğmesine tıklayın.

 **Birlikte çalışabilirlik** etkinlik Tasarımcısı **araç kutusundan** sürüklenip [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyine, örneğin <xref:System.Activities.Statements.Sequence> içinde olduğu gibi, her yerde bırakılmış olarak bırakılabilir. Bu, birlikte çalışma için varsayılan **DisplayName** olan bir <xref:System.Activities.Statements.Interop> etkinliği oluşturur. @No__t_0, **birlikte çalışma** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

 **Gezinmek Için tıklama düğmesine tıklayın...** **bir .NET türü ve seçme** iletişim kutusunu açmak Için, **birlikte çalışma** Etkinlik tasarımcısında veya özellik kılavuzunda, **ActivityType** kutusundaki metin. Yalnızca iş akışı 3,0 veya iş akışı 3,5 etkinlikleri için türler gösterilir (yani yalnızca <xref:System.Workflow.ComponentModel.Activity> türetilen türler). bir tür belirtmek için bu kutuyu kullanarak [!INCLUDE[crabout](../includes/crabout-md.md)], bkz. [.NET türü ve seçme Iletişim kutusu](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md) konusu.

### <a name="the-interop-properties"></a>Birlikte çalışma özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.Interop> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzunda veya [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyinde düzenlenebilir.

|Özellik adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|@No__t_0 etkinliğinin kolay adı. Varsayılan olarak birlikte çalışabilirlik ' dir. Görünen ad kesinlikle gerekli olmasa da, bir görünen ad kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|Doğru|@No__t_0 etkinliğinin içerdiği etkinliğin türünü belirtir. Belirtilen bu tür <xref:System.Workflow.ComponentModel.Activity> türetmelidir.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Geçiş](../workflow-designer/migration-activity-designers.md)