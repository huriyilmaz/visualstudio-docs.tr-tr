---
title: 'Nasıl yapılır: örnekleme olaylarını seçme | Microsoft Docs'
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779057"
---
# <a name="how-to-choose-sampling-events"></a>Nasıl yapılır: örnekleme olaylarını seçme
Varsayılan olarak, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları, profili oluşturulmuş işlem tarafından kullanılan işlemci döngüsü sayısı olarak belirtilen bir aralıkta performans verilerini toplar. Bir aralıktaki varsayılan döngü sayısı 10.000.000 ' dir ve 1 GH bir bilgisayarda yaklaşık 0,01 saniyedir. Bir aralıktaki döngü sayısını değiştirebilir ve örnek olayı değiştirebilirsiniz. Aşağıdaki örnek olaylar mevcuttur:

- Saat döngüleri-CPU ile bağlantılı sorunlar için.

- Sayfa hataları-bellekle ilgili sorunlar için.

- Sistem çağrıları-g/ç ile ilgili sorunlar için.

- Performans sayacı-düşük düzeydeki performans sorunları için CPU sayaçları.

> [!IMPORTANT]
> Örnekleme yöntemini kullanarak .NET bellek verileri (ayırmalar veya nesne yaşam süreleri veya her ikisi de) topluyorsanız, Kullanıcı tarafından belirtilen tüm örnekleme olayları yok sayılır ve uygun bellek ayırmaları veya çöp toplama olayları ya da her ikisi de veri toplamak için kullanılır.

### <a name="to-select-a-sample-event"></a>Örnek bir olay seçmek için

1. **Performans Gezgini**, performans oturumuna sağ tıklayın ve ardından **Özellikler**' e tıklayın.

2. **Özellik sayfalarında** **örnekleme** özelliklerine tıklayın.

3. **Örnek olay** açılan listesinden, uygulamanızı profili eklemek için kullanmak istediğiniz örnek olayı seçin.

    > [!NOTE]
    > **Kullanılabilir performans sayaçları** yalnızca **örnek olay** açılan listesinden **performans sayacı** ' nı seçtiğinizde etkinleştirilir.

4. **Performans sayacı**' nı seçerseniz, **kullanılabilir performans sayaçları** ağaç görünümü denetiminden belirli bir CPU sayacı seçin.

    - **Taşınabilir olaylar** düğümündeki sayaçlar tüm işlemci türlerinde kullanılabilir.

    - **Platform olayları** düğümündeki sayaçlar, geçerli bilgisayardaki işlemciye özeldir ve diğer işlemci türlerinde kullanılamayabilir.

5. Örnek bir olay seçtiğinizde, **örnekleme aralığı** metin kutusunda varsayılan bir örnekleme aralığı değeri görüntülenir. Gerekirse, metin kutusuna istediğiniz değeri girebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)
- [Nasıl yapılır: Toplama metotlarını seçme](../profiling/how-to-choose-collection-methods.md)
- [CPU ve Windows sayaçları](../profiling/cpu-and-windows-counters.md)
- [Örnekleme veri değerlerini anlama](../profiling/understanding-sampling-data-values.md)
- [Komut satırından profil](../profiling/using-the-profiling-tools-from-the-command-line.md)
