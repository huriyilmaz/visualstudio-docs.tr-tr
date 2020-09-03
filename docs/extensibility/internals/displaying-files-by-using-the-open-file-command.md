---
title: Dosya Aç komutunu kullanarak dosyaları görüntüleme | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708592"
---
# <a name="display-files-by-using-the-open-file-command"></a>Dosya Aç komutunu kullanarak dosyaları görüntüleme
Aşağıdaki adımlarda IDE 'nin içindeki **Dosya** menüsünde bulunan **Açık dosya** komutunu nasıl işlediği açıklanır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Bu adımlar, projelerin bu komuttan kaynaklanan çağrılara nasıl yanıt vereceğini de açıklamaktadır.

 Bir Kullanıcı **Dosya** menüsündeki **Dosya Aç** komutuna tıkladığında ve **Dosya Aç** iletişim kutusundan bir dosya seçtiğinde aşağıdaki işlem gerçekleşir:

1. Çalışan belge tablosunu kullanarak IDE, dosyanın zaten bir projede açık olup olmadığını belirler.

    - Dosya açıksa, IDE pencereyi kapatır.

    - Dosya açık değilse, IDE her bir projeyi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> sorgulamak için çağırır ve dosyayı hangi projenin açabilceğini tespit edebilir.

        > [!NOTE]
        > Proje uygulamanızda <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> , projenizin dosyayı açtığı düzeyi gösteren bir öncelik değeri sağlayın. Öncelik değerleri <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> numaralandırmada verilmiştir.

2. Her proje, projenin dosyayı açmak için yaptığı önem derecesini gösteren bir öncelik düzeyiyle yanıt verir.

3. IDE, dosyayı hangi projenin açtığını öğrenmek için aşağıdaki ölçütleri kullanır:

    - En yüksek öncelik () ile yanıt veren proje `DP_Intrinsic` , dosyasını açar. Bu önceliğe sahip birden fazla proje yanıt verirse, yanıt veren ilk proje dosyasını açar.

    - En yüksek önceliğe () sahip hiçbir proje yanıt `DP_Intrinsic` vermezse, ancak tüm projeler aynı ve daha düşük önceliğe sahip olursa, etkin proje dosyayı açar. Etkin bir proje yoksa, yanıt veren ilk proje dosyayı açar.

    - Hiçbir proje, dosyanın () sahipliğini talep etmez `DP_Unsupported` , Miscellaneous Files projesi dosyayı açar.

         Çeşitli dosyalar projesinin bir örneği oluşturulursa, proje her zaman değeriyle yanıt verir `DP_CanAddAsExternal` . Bu değer, projenin dosyayı açabildiğini gösterir. Bu proje, başka bir projede yer alan dosyaları açmak için kullanılır. Bu projedeki öğelerin listesi kalıcı değil; Bu proje yalnızca bir dosyayı açmak için kullanıldığında **Çözüm Gezgini** görünür.

         Çeşitli dosyalar projesi dosyayı açabileceğini belirtmezse, projenin bir örneği oluşturulmamış demektir. Bu durumda, IDE çeşitli dosyalar projesinin bir örneğini oluşturur ve projeye dosyayı açmasını söyler.

4. IDE, dosyayı hangi projenin açtığını belirler, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> Bu proje üzerinde yöntemi çağırır.

5. Projenin ardından projeye özgü bir düzenleyici veya standart düzenleyici kullanarak dosyayı açma seçeneği vardır. Daha fazla bilgi için bkz. [nasıl yapılır: projeye özgü düzenleyicileri açma](../../extensibility/how-to-open-project-specific-editors.md) ve [nasıl yapılır: sırasıyla standart düzenleyiciler açma](../../extensibility/how-to-open-standard-editors.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Birlikte Aç komutunu kullanarak dosyaları görüntüleme](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)
- [Proje öğelerini aç ve Kaydet](../../extensibility/internals/opening-and-saving-project-items.md)
- [Nasıl yapılır: projeye özgü düzenleyiciler açma](../../extensibility/how-to-open-project-specific-editors.md)
- [Nasıl yapılır: standart düzenleyiciler açma](../../extensibility/how-to-open-standard-editors.md)
