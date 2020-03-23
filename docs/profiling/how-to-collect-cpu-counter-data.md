---
title: 'Nasıl Kullanılır: CPU Karşı Veri Toplama | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.cpucounters
helpviewer_keywords:
- profiling tools, using portable CPU counters
- performance tools, portable CPU counters
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 98291051a135a95ab72b4c3bfa09743d9620b94e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776377"
---
# <a name="how-to-collect-cpu-counter-data"></a>Nasıl yapılır: CPU sayaç verileri toplama

Donanıma özgü performans verilerini toplamak için cpu olay sayacı kullanılır. Bu makalede, enstrümantasyon profil oluşturma yöntemini kullandığınızda olay sayacı verilerinin nasıl toplandığı gösterilmektedir.

İki tür CPU karşı olayı oluşur:

- Taşınabilir olaylar - Belirli CPU'dan bağımsız olarak toplanabilen CPU olayları.

- Platform olayları - Belirli bir CPU ile birleşen CPU olayları.

  Taşınabilir olaylar, Kullanımdan Kaldırılan ve Durdurulmayan Döngüler, CPU arabellek olayları, dallanma olayları ve L2 önbellek olayları gibi genel olayları içerir. Kullanılabilir platform olay sayaçları işlemci üreticisi tarafından belirlenir.

  Etkinlik kategorileri taşınabilir ve platform sayaçları arasında paylaşılabilir. Örneğin, aşağıdaki veri kategorileri her iki tür için de sık sık kullanılır:

- Hafıza olayları.

- Ön uç olayları.

- Dal olayları.

  Profil oluşturucuda performans sayacı verilerini iki şekilde toplayabilirsiniz:

- Enstrümantasyona göre profil yaptığınızda bir veya daha fazla sayaçtan veri toplayın.

- Örnekleme profili nde örnekleme aralığı olarak bir sayaç olayı belirtin. Daha fazla bilgi için [bkz: Örnekleme olaylarını seçin.](../profiling/how-to-choose-sampling-events.md)

## <a name="to-collect-cpu-performance-counter-data-when-you-profile-by-instrumentation"></a>Enstrümantasyona göre profil çıkarırken CPU performans sayacı verilerini toplamak için

1. Performans oturumu **Özellik Sayfalarında** **CPU Sayaçları'nı tıklatın.**

2. CPU **Sayaçları Topla** onay kutusunu seçin.

3. Toplamak istediğiniz örnek olayları bulana kadar **Kullanılabilir performans sayaçları** ağacını genişletin.

4. Toplamak istediğiniz her olay için olayı seçin ve ardından **etkinliği Seçili Sayaçlar** listesine eklemek için sağ oku tıklatın.

    > [!NOTE]
    > **Kullanılabilir performans sayaçları** yalnızca CPU **sayaçlarını topla** onay kutusunu seçerseniz etkinleştirilir.

## <a name="see-also"></a>Ayrıca bkz.

[Performans oturumlarını](../profiling/configuring-performance-sessions.md)
yapılandırma[Performans oturumu özellikleri](../profiling/performance-session-properties.md)
[CPU ve Windows sayaçları](../profiling/cpu-and-windows-counters.md)
[Nasıl seçilir: Örnekleme olaylarını seçme](../profiling/how-to-choose-sampling-events.md)
