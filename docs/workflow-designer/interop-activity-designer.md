---
title: İş Akışı Tasarımcısı-Interop etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8047df3787c0871e369b6079e4f0cc80f6d93949
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650205"
---
# <a name="interop-activity-designer"></a>Interop Etkinlik Tasarımcısı

**Birlikte çalışabilirlik** etkinlik Tasarımcısı, bir <xref:System.Activities.Statements.Interop> etkinliği oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-interop-activity"></a>Birlikte çalışma etkinliği

@No__t_0 etkinliği, bir iş akışı içinde <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> türetilen türlerin yürütülmesini yönetir.

### <a name="use-the-interop-activity-designer"></a>Birlikte çalışabilirlik etkinlik tasarımcısını kullanma

**Birlikte çalışma** etkinliği Tasarımcısı **, araç kutusu sekmesine** tıklanarak erişilen **araç kutusu** **geçiş** kategorisinde bulunabilir. alternatif olarak, **Görünüm** menüsünden **araç kutusu** 'nu seçin veya CTRL tuşuna basın+**alt** +**X**.

@No__t_1 etkinliğini içeren [geçiş](../workflow-designer/migration-activity-designers.md) kategorisi yalnızca, projeniz .NET Framework 4 (tam) veya üzerini hedeflerse **araç kutusu** 'nda görüntülenir. Gerekirse, projenizin hedeflediği Framework sürümünü değiştirebilirsiniz.

**Birlikte çalışabilirlik** etkinlik Tasarımcısı, **araç kutusu** 'ndan sürüklenebilir ve etkinliklerin genellikle yerleştirildiği her yerde (bir <xref:System.Activities.Statements.Sequence> içinde) iş akışı Tasarımcısı yüzeyine bırakılabilir. **Birlikte çalışma** etkinlik Tasarımcısı 'nın atılması, birlikte çalışma öğesinin varsayılan **DisplayName** değeriyle bir <xref:System.Activities.Statements.Interop> etkinliği oluşturur. **Birlikte çalışma** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda <xref:System.Activities.Activity.DisplayName%2A> düzenleyebilirsiniz.

**Bir .NET türü görüntüle ve Seç** iletişim kutusunu açmak Için, **birlikte çalışma** Etkinlik tasarımcısında veya özellik kılavuzunda, **ActivityType** kutusunda bulunan metne gitmek **için tıklayın** . Yalnızca iş akışı 3,0 veya iş akışı 3,5 etkinlikleri için türler gösterilir. Diğer bir deyişle, yalnızca <xref:System.Workflow.ComponentModel.Activity> türetilen türler gösterilir. Bir tür belirtmek için bu kutuyu kullanma hakkında daha fazla bilgi için bkz. [bir .NET türü Için tarama ve seçme Iletişim kutusu](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md).

### <a name="the-interop-properties"></a>Birlikte çalışma özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.Interop> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzunda veya İş Akışı Tasarımcısı yüzeyinde düzenlenebilir.

|Özellik adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|@No__t_0 etkinliğinin kolay adı. Varsayılan değer **birlikte çalışabilirlik**' dir. Görünen ad gerekli olmasa da, bir tane sağlamanız önerilir.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|Doğru|@No__t_0 etkinliğinin içerdiği etkinliğin türünü belirtir. Belirtilen bu tür <xref:System.Workflow.ComponentModel.Activity> türetmelidir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Geçiş](../workflow-designer/migration-activity-designers.md)