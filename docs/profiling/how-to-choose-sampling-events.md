---
title: 'Nasıl seçilir: Örnekleme Etkinlikleri | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.sampling
helpviewer_keywords:
- clock cycles sample event
- sample events, choosing
- profiling tools, sample events
- page faults sample event
- system calls sample event
- performance counter sample event
- performance tools, sample events
ms.assetid: ce7cb734-80ac-4930-a4ef-e24395e1cc07
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 82462ae5052150da7761dfcd855e5339e1b7d821
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779057"
---
# <a name="how-to-choose-sampling-events"></a>Nasıl seçilir: Örnekleme olaylarını seçin
Varsayılan olarak, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları, profillenmiş işlem tarafından kullanılan işlemci döngüleri sayısı olarak belirtilen bir aralıkta performans verileri toplar. Bir aralıktaki varsayılan döngü sayısı 10.000.000'dir ve bu da 1 GH'lik bir bilgisayarda yaklaşık 0,01 saniyedir. Döngü sayısını bir aralıkta değiştirebilir ve örnek olayı değiştirebilirsiniz. Aşağıdaki örnek olaylar mevcuttur:

- Saat döngüleri - CPU'ya bağlı sorunlar için.

- Sayfa hataları - bellekle ilgili sorunlar için.

- Sistem aramaları - G/Ç ile ilgili sorunlar için.

- Performans sayacı - Düşük düzeyperformans sorunları için CPU sayaçları.

> [!IMPORTANT]
> Örnekleme yöntemini kullanarak .NET bellek verilerini (ayırmalar veya nesne yaşam alanları veya her ikisi) topluyorsanız, kullanıcı tarafından belirtilen tüm örnekleme olayları göz ardı edilir ve veri toplamak için uygun bellek ayırmaları veya çöp toplama olayları veya her ikisi de kullanılır.

### <a name="to-select-a-sample-event"></a>Örnek bir olay seçmek için

1. **Performans Gezgini'nde,** performans oturumuna sağ tıklayın ve ardından **Özellikler'i**tıklatın.

2. Özellik **Sayfalarında,** **Örnekleme** özelliklerini tıklatın.

3. Örnek **olay** açılır listesinden, uygulamanızın profilini çıkarmak için kullanmak istediğiniz örnek olayı seçin.

    > [!NOTE]
    > **Kullanılabilir performans sayaçları** yalnızca **Örnek olay** açılır listesinden **Performans sayacını** seçerseniz etkinleştirilir.

4. **Performans sayacını**seçerseniz, **Kullanılabilir performans sayaçları** ağacı görünümü denetiminden belirli bir CPU sayacı seçin.

    - **Taşınabilir Olaylar** düğümündeki sayaçlar her tür işlemcide kullanılabilir.

    - **Platform Olayları** düğümündeki sayaçlar geçerli bilgisayardaki işlemciye özgüdür ve diğer işlemci türlerinde kullanılamayabilir.

5. Örnek bir olay seçtiğinizde, **Örnekleme aralığı** metin kutusunda varsayılan örnekleme aralığı değeri görüntülenir. Gerekirse, metin kutusuna istediğiniz değeri girebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)
- [Nasıl yapılır: Toplama yöntemlerini seçin](../profiling/how-to-choose-collection-methods.md)
- [CPU ve Windows sayaçları](../profiling/cpu-and-windows-counters.md)
- [Örnekleme veri değerlerini anlama](../profiling/understanding-sampling-data-values.md)
- [Komut satırından profil](../profiling/using-the-profiling-tools-from-the-command-line.md)
