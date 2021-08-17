---
title: CPU sayacı verilerini topla | Microsoft Docs
description: Donanıma özgü performans verilerini toplamak için CPU (donanım) olay sayaçlarını nasıl kullanacağınızı öğrenin. Bu makalede çeşitli olay türleri listelenmektedir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.cpucounters
helpviewer_keywords:
- profiling tools, using portable CPU counters
- performance tools, portable CPU counters
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 850a3ab4f238c0a95c5b01059eddee3f16b6b36034e382d9542bdaa5a243e359
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121333034"
---
# <a name="how-to-collect-cpu-counter-data"></a>Nasıl yapılır: CPU sayaç verileri toplama

Donanıma özgü performans verilerini toplamak için bir CPU olay sayacı kullanılır. Bu makalede, izleme profili oluşturma yöntemini kullandığınızda olay sayacı verilerinin nasıl toplanacağı gösterilmektedir.

İki tür CPU sayacı olayı oluşur:

- Taşınabilir olaylar-belirli bir CPU 'ya bakılmaksızın toplanabilecek CPU olayları.

- Platform olayları-belirli bir CPU ile bağlanmış CPU olayları.

Taşınabilir olaylar, kullanımdan kaldırılan yönergeler, durdurulmayan döngüler, CPU arabellek olayları, dallanma olayları ve L2 önbellek olayları gibi genel olayları içerir. Kullanılabilir platform olay sayaçları, işlemci üreticisi tarafından belirlenir.

Etkinlik kategorileri, taşınabilir ve Platform sayaçları arasında paylaşılabilir. Örneğin, aşağıdaki veri kategorileri genellikle her iki tür için ortaktır:

- Bellek olayları.

- Ön uç olayları.

- Dal olayları.

Profil Oluşturucu 'da performans sayacı verilerini iki şekilde toplayabilirsiniz:

- İzleme tarafından profil oluştururken bir veya daha fazla sayaçdan veri toplayın.

- Örneklemeye göre profil oluştururken örnekleme aralığı olarak bir sayaç olayı belirtin. Daha fazla bilgi için bkz. [nasıl yapılır: örnekleme olaylarını seçme](../profiling/how-to-choose-sampling-events.md).

## <a name="to-collect-cpu-performance-counter-data-when-you-profile-by-instrumentation"></a>İzleme ile profil oluşturduğunuzda CPU performans sayacı verilerini toplamak için

1. Performans oturumu **özellik sayfalarında** **CPU sayaçları** ' na tıklayın.

2. **CPU sayaçlarını topla** onay kutusunu seçin.

3. Toplamak istediğiniz örnek olayları bulana kadar, **kullanılabilir performans sayaçları** ağacını genişletin.

4. Toplamak istediğiniz her olay için, olayı seçin ve ardından sağ oka tıklayarak olayı **Seçili sayaçlar** listesine ekleyin.

    > [!NOTE]
    > **Kullanılabilir performans sayaçları** yalnızca **CPU sayaçlarını topla** onay kutusunu seçerseniz etkindir.

## <a name="see-also"></a>Ayrıca bkz.

[Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md) 
 [Performans oturumu özellikleri](../profiling/performance-session-properties.md) 
 [CPU ve Windows sayaçları](../profiling/cpu-and-windows-counters.md) 
 [Nasıl yapılır: örnekleme olaylarını seçme](../profiling/how-to-choose-sampling-events.md)
