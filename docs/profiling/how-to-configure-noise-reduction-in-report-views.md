---
title: Rapor Görünümlerinde Gürültü Azaltmayı | Microsoft Docs
description: Gürültüyü azaltmak ve raporlarınız için performans sorunlarını daha belirgin hale düşürmek için kırpma ve katlamanın her ikisi de varsayılan olarak etkindir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.noisereduction.dialog
helpviewer_keywords:
- profiling tools, trimming
- profiling tools, report noise reduction
- profiling tools, folding
ms.assetid: b07e0375-bb73-47e3-8d1d-b9b492fb16c9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 015ea700cca87912013b5b12c3d9e2ead78a0c54
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122038857"
---
# <a name="how-to-configure-noise-reduction-in-report-views"></a>Nasıl yapılandırılır: Rapor görünümlerinde gürültü azaltmayı yapılandırma
Performans raporları, Çağrı Ağacı görünümünde ve Ayırma görünümünde sunulan veri miktarını sınırlandırarak gürültü azaltma için yalıtabilirsiniz. Gürültü azaltmayı kullanarak performans sorunları daha belirgin hale geliyor. Bu, performans raporlarını analiz etmek için kullanışlıdır.

 Gürültü azaltma yapılandırma seçenekleri aşağıdaki ayarları içerir:

- **Kırpma** Bir rapor analiz edilirken görünüm, aşağıdaki kırpma yordamında açıklandığı gibi yapılandırmış olduğu değer ve eşik ayarlarında yer alan işlevleri atlar. Kırpma varsayılan olarak etkindir.

- **Katlama** Katlamayı etkinleştirirsanız, yapılandırmış olduğunuz ayarlara uygun bir yolda ardışık işlevler, aşağıdaki katlama yordamında açıklandığı gibi birleştirilir. Katlama varsayılan olarak etkindir.

### <a name="to-configure-trimming-for-a-performance-report"></a>Performans raporu için kırpmayı yapılandırmak için

1. Oluşturulan raporda bir Çağrı Ağacı görünümü veya Ayırma görünümü görüntülendiğinde, Geliştirici  menüsünde ProfilLeyici'ye ve ardından Gürültü Azaltma **Seçenekleri'ne tıklayın.** 

     Gürültü **Azaltma iletişim** kutusu görüntülenir.

2. Kırpmayı etkinleştirmek için şu adımları izleyin:

    1. Kırpmayı **Etkinleştir'i seçin.** Bu varsayılan ayardır.

        > [!NOTE]
        > Gürültü azaltma etkinleştirilirse raporda bir bilgi çubuğu görüntülenir. Daha fazla bilgi için [bkz. Çağrı Ağacı Görünümü](../profiling/call-tree-view.md) [ve Ayırmalar Görünümü.](../profiling/dotnet-memory-allocations-view.md)

    2. Değer açılan listesini kullanarak ve **uygun** ayarı seçerek değer ayarını yapılandırabilirsiniz.

    3. Eşik metin kutusuna bir yüzde değeri yazarak istenen **eşik ayarını** yapılandırma.

    4. Oluşturulan raporda gürültü azaltma uyarılarını etkinleştirmek için, Gürültü Azaltma **etkinleştirildiğinde uyarıyı görüntüle'yi seçin.** Bu varsayılan ayardır.

3. Kırpmayı devre dışı bırakmak için **Kırpmayı Etkinleştir'in ().**

4. **Tamam**'a tıklayın.

### <a name="to-configure-folding-for-a-performance-report"></a>Performans raporu için katlama yapılandırmak için

1. Geliştirici  menüsünde ProfilLeyici'ye **ve ardından** Gürültü Azaltma **Seçenekleri'ne tıklayın.**

     Gürültü **Azaltma iletişim** kutusu görüntülenir.

2. Katlamayı etkinleştirmek için şu adımları izleyin:

    1. **Katlamayı Etkinleştir'i seçin.** Bu varsayılan ayardır.

        > [!NOTE]
        > Gürültü azaltma etkinleştirilirse raporda bir bilgi çubuğu görüntülenir. Daha fazla bilgi için [bkz. Çağrı Ağacı Görünümü](../profiling/call-tree-view.md) [ve Ayırmalar Görünümü.](../profiling/dotnet-memory-allocations-view.md)

    2. Değer açılan listesini kullanarak **ve** ilgili ayarı seçerek değer ayarını yapılandırabilirsiniz.

    3. Eşik metin kutusuna bir yüzde değeri yazarak istenen **eşik ayarını** yapılandırma.

    4. Oluşturulan raporda gürültü azaltma uyarılarını etkinleştirmek için, Gürültü Azaltma **etkinleştirildiğinde uyarıyı görüntüle'yi seçin.** Bu varsayılan ayardır.

3. Katlama özelliğini devre dışı bırakmak için **Katlamayı Etkinleştir'i temizlayın.**

4. **Tamam**'a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Performans araçları rapor görünümlerini özelleştirme](../profiling/customizing-performance-tools-report-views.md)
- [Nasıl yapılır: Kısa işlevleri izlemeden hariç tutma veya izlemeye dahil etme](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)
- [Çağrı Ağacı Görünümü](../profiling/call-tree-view.md)
- [Ayırmalar Görünümü](../profiling/dotnet-memory-allocations-view.md)
