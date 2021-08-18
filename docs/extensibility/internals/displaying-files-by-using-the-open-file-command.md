---
title: Dosya Aç Komut Satırı Kullanarak Dosyaları Görüntüleme | Microsoft Docs
description: Tümleştirilmiş Visual Studio ortamının (IDE) Dosyaları görüntülemek için Dosya menüsündeki Dosya Aç komutunu nasıl işlemektedir?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: b9ba1acd9a1a918e70bf8ac71fb6a1d9e40a2231
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122050082"
---
# <a name="display-files-by-using-the-open-file-command"></a>Dosya Aç komutunu kullanarak dosyaları görüntüleme
Aşağıdaki adımlar, IDE'nin dosyasındaki Dosya menüsünde **bulunan** Dosya Aç komutunu nasıl **işley** olduğunu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] açıklar. Adımlarda ayrıca projelerin bu komuttan gelen çağrılara nasıl yanıt vermeleri gerektiği de anlatılacaktır.

 Kullanıcı Dosya **menüsündeKi Dosya Aç** **komutuna** tıklar ve Dosya  Aç iletişim kutusundan bir dosya seçerken aşağıdaki işlem gerçekleşir:

1. Çalışan belge tablosu kullanılarak IDE, dosyanın bir projede zaten açık olup olmadığını belirler.

    - Dosya açıksa IDE pencereyi yeniden açar.

    - Dosya açık değilse, IDE hangi projenin dosyayı aça olduğunu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> belirlemek için her projeyi sorgulamaya çağrır.

        > [!NOTE]
        > projenizin <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> uygulamasında, projenizin dosyayı açtığı düzeyi gösteren bir öncelik değeri sağlar. Öncelik değerleri, <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> numaralamada sağlanır.

2. Her proje, dosyayı açmak için projenin ne kadar önemli olduğunu belirten bir öncelik düzeyiyle yanıt verir.

3. IDE, dosyayı açan projeyi belirlemek için aşağıdaki ölçütleri kullanır:

    - En yüksek önceliğe ( ) sahip yanıt `DP_Intrinsic` veren proje dosyasını açar. Birden fazla proje bu öncelikle yanıt verirse, yanıt veren ilk proje dosyasını açar.

    - Hiçbir proje en yüksek önceliğe sahip ( ) yanıt vermiyorsa ama tüm projeler aynı, daha düşük önceliğe sahip yanıt `DP_Intrinsic` vermiyorsa, etkin proje dosyayı açar. Etkin proje yoksa, yanıt veren ilk proje dosyasını açar.

    - Herhangi bir proje dosyanın sahipliğini talep yoksa ( ), Çeşitli `DP_Unsupported` Dosyalar projesi dosyayı açar.

         Çeşitli Dosyalar projesinin bir örneği oluşturulursa, proje her zaman değeriyle yanıt `DP_CanAddAsExternal` verir. Bu değer, projenin dosyayı aça olduğunu gösterir. Bu proje, başka bir projede yer alan açık dosyaları ev olarak kabul etmek için kullanılır. Bu projedeki öğelerin listesi kalıcı değil; Bu proje, **Çözüm Gezgini** yalnızca bir dosyayı açmak için kullanılırken görünür.

         Çeşitli Dosyalar projesi, dosyayı açanın belirteci yoksa, projenin bir örneği oluşturulmaz. Bu durumda IDE, Çeşitli Dosyalar projesinin bir örneğini oluşturur ve projeye dosyayı açması için bunu söyler.

4. IDE, dosyayı hangi projenin açtığını belirler belirlemez, bu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> proje üzerinde yöntemini çağırır.

5. Ardından proje, projeye özgü bir düzenleyici veya standart düzenleyici kullanarak dosyayı açma seçeneğine sahip olur. Daha fazla bilgi [için, sırasıyla Bkz. Nasıl](../../extensibility/how-to-open-project-specific-editors.md) 2019: Projeye özgü düzenleyicileri açma ve Nasıl 2019'da standart [düzenleyicileri](../../extensibility/how-to-open-standard-editors.md)açma.

## <a name="see-also"></a>Ayrıca bkz.
- [Birlikte Aç komutunu kullanarak dosyaları görüntüleme](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)
- [Proje öğelerini açma ve kaydetme](../../extensibility/internals/opening-and-saving-project-items.md)
- [Nasıllı: Projeye özgü düzenleyicileri açma](../../extensibility/how-to-open-project-specific-editors.md)
- [Nasıl: Standart düzenleyicileri açma](../../extensibility/how-to-open-standard-editors.md)
