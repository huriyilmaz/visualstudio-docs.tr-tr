---
title: Dosya Yı Kullanarak Dosyaları Görüntüleme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cc18442c55b6989c4d8668e1425fdd62a2d4b1b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708592"
---
# <a name="display-files-by-using-the-open-file-command"></a>Dosya aç komutunu kullanarak dosyaları görüntüleme
Aşağıdaki adımlar, IDE'nin [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Dosya** menüsünde bulunan Dosya **Yı aç** komutunu nasıl işleyeceğini açıklar. Adımlar, projelerin bu komuttan kaynaklanan çağrılara nasıl yanıt vermesi gerektiğini de açıklar.

 Bir kullanıcı **Dosya** menüsünde **Dosya Aç** komutunu tıklattığında ve **Dosya aç** iletişim kutusundan bir dosya seçtiğinde aşağıdaki işlem gerçekleşir:

1. Çalışan belge tablosunu kullanarak, IDE dosyanın bir projede zaten açık olup olmadığını belirler.

    - Dosya açıksa, IDE pencereyi yeniden yüzeye çıkar.

    - Dosya açık değilse, Hangi projenin <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> dosyayı açabileceğini belirlemek için IDE her projeyi sorgulamaya çağırır.

        > [!NOTE]
        > Proje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>uygulamanızda, projenizin dosyayı açtığı düzeye işaret eden bir öncelik değeri sağlayın. Öncelik değerleri numaralandırmasağlanır. <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>

2. Her proje, dosyayı açmak için proje olmanın önemini gösteren bir öncelik düzeyiyle yanıt verir.

3. IDE, dosyayı hangi projenin açtığını belirlemek için aşağıdaki ölçütleri kullanır:

    - En yüksek öncelikle yanıt veren`DP_Intrinsic`proje ( ) dosyayı açar. Birden fazla proje bu öncelikle yanıt verirse, yanıt verecek ilk proje dosyayı açar.

    - Hiçbir proje en yüksek önceliğe`DP_Intrinsic`sahip yanıt vermiyorsa ( ), ancak tüm projeler aynı, daha düşük öncelikle yanıt veriyorsa, etkin proje dosyayı açar. Proje etkin değilse, yanıt verecek ilk proje dosyayı açar.

    - Hiçbir proje dosyanın sahipliğini`DP_Unsupported`talep ederse ( ), Çeşitli Dosyalar projesi dosyayı açar.

         Çeşitli Dosyalar projesinin bir örneği oluşturulursa, proje her zaman değerle `DP_CanAddAsExternal`yanıt verir. Bu değer, projenin dosyayı açabileceğini gösterir. Bu proje, başka bir projede olmayan açık dosyaları barındırmak için kullanılır. Bu projedeki öğelerin listesi kalıcı değildir; Bu proje, yalnızca bir dosyayı açmak için kullanıldığında **Çözüm Gezgini'nde** görünür.

         Çeşitli Dosyalar projesi dosyayı açabileceğini göstermiyorsa, projenin bir örneği oluşturulmadı. Bu durumda, IDE Çeşitli Dosyalar projesinin bir örneğini oluşturur ve projeye dosyayı açmasını söyler.

4. IDE dosyayı hangi projenin açtığını belirler belirlemez, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> bu projedeki yöntemi çağırır.

5. Proje daha sonra, projeye özgü bir düzenleyici veya standart bir düzenleyici kullanarak dosyayı açma seçeneğine sahiptir. Daha fazla bilgi için [bkz: Projeye özel editörleri ve](../../extensibility/how-to-open-project-specific-editors.md) [nasıl açılır: Standart düzenleyicileri](../../extensibility/how-to-open-standard-editors.md)sırasıyla açın.

## <a name="see-also"></a>Ayrıca bkz.
- [Ile Aç komutunu kullanarak dosyaları görüntüleme](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)
- [Proje öğelerini açma ve kaydetme](../../extensibility/internals/opening-and-saving-project-items.md)
- [Nasıl açılır: Projeye özel düzenleyicileri açın](../../extensibility/how-to-open-project-specific-editors.md)
- [Nasıl yapılsın: Standart düzenleyicileri açın](../../extensibility/how-to-open-standard-editors.md)
