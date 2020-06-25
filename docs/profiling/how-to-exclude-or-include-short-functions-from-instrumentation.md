---
title: Kısa işlevleri izlemeden hariç tutma veya izlemeye dahil etme
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profiling tools, instrument events
- profiling tools, include short functions
- profiling tools, exclude short functions
ms.assetid: eaeead79-aafe-4490-86ff-6ed4cad9c15f
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4aaae07987f1d3364b064465aa6edff9a4748301
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85329784"
---
# <a name="how-to-exclude-or-include-short-functions-from-instrumentation"></a>Nasıl yapılır: Kısa işlevleri izlemeden hariç tutma veya izlemeye dahil etme
Varsayılan olarak, profil oluşturma araçları *küçük işlevleri* izleme 'den hariç tutar. Küçük işlevler, hiçbir işlev çağrısı yapmayan kısa işlevlerdir. Bu küçük işlevleri dışlayarak daha az izleme yükü ve bu nedenle geliştirilmiş izleme hızı sağlanır. Küçük işlevlerin dışlamasıdır, performans profil oluşturma veri dosyasını da azaltır (.* VSP*), analiz için gereken süre ve zaman. Küçük işlevler dışlanmazsa, küçük işlevlerde harcanan süre üst işlevlerinin dışlanması ve dahil zamanına göre sayılır. Küçük işlevler, aşağıdaki yordamda açıklandığı gibi, izleme halinde dışarıda bırakılabilirler.

### <a name="to-exclude-or-include-short-functions-from-instrumentation"></a>Araçlardan kısa işlevleri dışlamak veya dahil etmek için

1. **Performans Gezgini**' de, **performans oturumu** ' nu seçin ve ardından sağ tıklayıp **Özellikler**' i seçin.

     **Özellik Sayfaları** iletişim kutusu görüntülenir.

2. **Özellik sayfalarında**, **izleme** özelliklerine tıklayın.

3. Kısa işlevleri izleme 'den dışlamak için, **kısa Işlevleri izleme 'Den hariç tut**' u seçin. Bu varsayılan ayardır.

     -veya-

     Araçdaki kısa işlevleri eklemek için, **kısa Işlevleri izleme**' yi temizleyin.

4. **Tamam**'a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Veri toplamayı denetleme](../profiling/controlling-data-collection.md)
- [Performans oturumu özellikleri](../profiling/performance-session-properties.md)
