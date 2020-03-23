---
title: Kısa işlevleri izlemeden hariç tutma veya izlemeye dahil etme
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: de6d6325b1e518146768798c773754c091861aa8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74775920"
---
# <a name="how-to-exclude-or-include-short-functions-from-instrumentation"></a>Nasıl yapılır: Kısa işlevleri izlemeden hariç tutma veya izlemeye dahil etme
Varsayılan olarak, Profil Oluşturma araçları *küçük işlevleri* enstrümantasyondan hariç tutar. Küçük işlevler, herhangi bir işlev çağrısı yapmayan kısa işlevlerdir. Bu küçük işlevlerin dışında daha az enstrümantasyon yükü ve bu nedenle gelişmiş enstrümantasyon hızı sağlar. Küçük işlevlerin dışlanması da performans profil oluşturma veri dosyasını azaltır (.* vsp*) boyutu ve analiz için gerekli olan süre. Küçük işlevler dışlanırsa, küçük işlevlerde harcanan süre, üst işlevlerinin özel ve kapsayıcı zamanına göre sayılır. Aşağıdaki yordamda açıklandığı gibi küçük işlevler dışlanabilir veya enstrümantasyona dahil edilebilir.

### <a name="to-exclude-or-include-short-functions-from-instrumentation"></a>Enstrümantasyondan kısa işlevleri dışlamak veya dahil etmek için

1. **Performans Gezgini'nde,** **Performans Oturumu'nü** seçin ve ardından Sağ tıklatın ve **Özellikler'i**seçin.

     **Özellik Sayfaları** iletişim kutusu görüntülenir.

2. Özellik **Sayfalarında,** **Enstrümantasyon** özelliklerini tıklatın.

3. Kısa işlevleri enstrümantasyondan dışlamak için, **Kısa işlevleri Enstrümantasyon'dan Hariç Tut'u'nun** Bu varsayılan ayardır.

     -veya-

     Enstrümantasyona kısa işlevleri dahil etmek için, **enstrümantasyondan kısa işlevleri hariç tut'** un açıklığı.

4. **Tamam**'a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Veri toplamayı denetleme](../profiling/controlling-data-collection.md)
- [Performans oturumu özellikleri](../profiling/performance-session-properties.md)
