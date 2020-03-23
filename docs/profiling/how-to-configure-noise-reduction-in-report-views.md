---
title: 'Nasıl Yapılandırılır: Rapor Görünümlerinde Gürültü AzaltmaYı Yapılandırma | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.noisereduction.dialog
helpviewer_keywords:
- profiling tools, trimming
- profiling tools, report noise reduction
- profiling tools, folding
ms.assetid: b07e0375-bb73-47e3-8d1d-b9b492fb16c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ccfb9dab504bc3fa9405bb56c9fce82ed18820ac
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776338"
---
# <a name="how-to-configure-noise-reduction-in-report-views"></a>Nasıl yapilir: Rapor görünümlerinde gürültü azaltmayı yapılandırma
Performans raporları, Çağrı Ağacı görünümünde ve Tahsisat görünümünde sunulan veri miktarını sınırlayarak gürültü azaltma için yapılandırılabilir. Gürültü azaltma kullanılarak performans sorunları daha belirgin hale gelen performans sorunları dır. Bu, performans raporlarını çözümlediğinizde yararlıdır.

 Gürültü azaltma yapılandırma seçenekleri aşağıdaki ayarları içerir:

- **Kırpma** Bir rapor çözümlendiğinde, görünüm, aşağıdaki kırpma yordamında açıklandığı gibi, yapılandırdığınız değer ve eşik ayarlarında düşen işlevleri atlar. Varsayılan olarak, kırpma etkindir.

- **Katlama** Katlamayı etkinleştirirseniz, yapılandırmayaptığınız ayarları karşılayan bir yolda ardışık işlevler, aşağıdaki katlama yordamında açıklandığı gibi birleştirilir. Varsayılan olarak, katlama varsayılan olarak etkinleştirilir.

### <a name="to-configure-trimming-for-a-performance-report"></a>Performans raporu için kırpma yapılandırmak için

1. Oluşturulan raporda Çağrı Ağacı görünümü veya Tahsisat görünümü görüntülendiğinde, **Geliştirici** menüsünde **Profiler'ı** tıklatın ve ardından **Gürültü Azaltma Seçenekleri'ni**tıklatın.

     **Gürültü Azaltma** iletişim kutusu görüntülenir.

2. Kırpmayı etkinleştirmek için aşağıdaki adımları izleyin:

    1. **Kırpmayı Etkinleştir'i**seçin. Bu varsayılan ayardır.

        > [!NOTE]
        > Gürültü azaltma etkinse, raporda bir bilgi çubuğu görüntülenir. Daha fazla bilgi için [Bkz. Çağrı Ağacı Görünümü](../profiling/call-tree-view.md) ve [Tahsisler Görünümü.](../profiling/dotnet-memory-allocations-view.md)

    2. **Değer** açılır listesini kullanarak ve ilgili ayarı seçerek değer ayarını yapılandırın.

    3. **Eşik** metin kutusuna yüzde değeri yazarak istenen eşik ayarını yapılandırın.

    4. Oluşturulan raporda gürültü azaltma uyarısını etkinleştirmek **için, Gürültü Azaltma etkinleştirildiğinde Görüntüle'yi seçin.** Bu varsayılan ayardır.

3. Kırpmayı devre dışı kalmak için Kırpmayı **Etkinleştir'i**temizleyin.

4. **Tamam**'a tıklayın.

### <a name="to-configure-folding-for-a-performance-report"></a>Performans raporu için katlama yapılandırmak için

1. **Geliştirici** menüsünde **Profiler'ı** tıklatın ve ardından **Gürültü Azaltma Seçenekleri'ni**tıklatın.

     **Gürültü Azaltma** iletişim kutusu görüntülenir.

2. Katlamayı etkinleştirmek için aşağıdaki adımları izleyin:

    1. **Katlayı etkinleştir'i**seçin. Bu varsayılan ayardır.

        > [!NOTE]
        > Gürültü azaltma etkinse, raporda bir bilgi çubuğu görüntülenir. Daha fazla bilgi için [Bkz. Çağrı Ağacı Görünümü](../profiling/call-tree-view.md) ve [Tahsisler Görünümü.](../profiling/dotnet-memory-allocations-view.md)

    2. **Değer** açılır listesini kullanarak ve ilgili ayarı seçerek değer ayarını yapılandırın.

    3. **Eşik** metin kutusuna yüzde değeri yazarak istenen eşik ayarını yapılandırın.

    4. Oluşturulan raporda gürültü azaltma uyarısını etkinleştirmek **için, Gürültü Azaltma etkinleştirildiğinde Görüntüle'yi seçin.** Bu varsayılan ayardır.

3. Katlama devre dışı katlamak için, açık **Katla' yı etkinleştirin.**

4. **Tamam**'a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Performans araçlarını rapor görünümlerini özelleştirme](../profiling/customizing-performance-tools-report-views.md)
- [Nasıl yapılır: Kısa işlevleri izlemeden hariç tutma veya izlemeye dahil etme](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)
- [Çağrı Ağacı Görünümü](../profiling/call-tree-view.md)
- [Ayırmalar Görünümü](../profiling/dotnet-memory-allocations-view.md)
