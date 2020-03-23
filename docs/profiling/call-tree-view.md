---
title: Çağrı Ağacı Görünümü | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.calltree
helpviewer_keywords:
- Call Tree view
- profiling tools reports, Call Tree view
- performance reports, Call Tree view
- profiling tools, Call Tree view
ms.assetid: b2dbc033-bf95-4d10-8e51-f9462979133e
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0b932d5f9e4a178c94f3e490c66cec64648ce4f6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773341"
---
# <a name="call-tree-view"></a>Çağrı Ağacı görünümü
Çağrı Ağacı görünümü, profilli uygulamada geçen işlev yürütme yollarını görüntüler. Ağacın kökü, uygulamaya veya bileşene giriş noktasıdır. Her işlev düğümü, aradığı tüm işlevleri ve bu işlev çağrılarıyla ilgili performans verilerini listeler.

 Çağrı Ağacı görünümü, en çok zaman tüketilen veya en sık örneklenmiş bir işlevin yürütme yolunu genişletebilir ve vurgulayabilir. En yüksek performans pahalı yolu görüntülemek için, işlevi sağ tıklatın ve ardından **Sıcak Yolu Genişlet'i**tıklatın.

 Profil oluşturma çalışmasındaki her işlem kök düğüm olarak görüntülenir. Başlangıç düğümü olarak ayarlamak istediğiniz düğümü sağ tıklatarak ve ardından **Root'u**Ayarla'yı seçerek Çağrı Ağacı görünümünün başlangıç düğümünü ayarlayabilirsiniz.

 Kök düğümünü ayarladığınızda, seçili düğümün alt ağacı dışında görünümdeki diğer tüm girişleri ortadan kaldırırsınız. Kök düğümünü görüntülediğiniz düğüme geri sıfırlayabilirsiniz. Çağrı Ağacı görünüm penceresinde, sağ tıklatın ve sonra **Root'u Sıfırla'yı**seçin.

 Çağrı Ağacı görünümü sütun eklemek veya kaldırmak için özelleştirilebilir. Sütun Adı **Başlık Çubuğu'nu**sağ tıklatın ve ardından **Sütun Ekle/Kaldır'ı**seçin.

 Çağrı Ağacı görünümü, sunulan veri miktarını sınırlayarak gürültü azaltma için yapılandırılabilir. Gürültü azaltma kullanılarak, performans sorunları görünümde daha belirgindir. Performans sorunlarını ayırt etmek kolay olduğunda, çözümleme daha kolaydır. Daha fazla bilgi için [bkz: Rapor görünümlerinde gürültü azaltmayı yapılandırma.](../profiling/how-to-configure-noise-reduction-in-report-views.md)

> [!NOTE]
> Gürültü azaltma etkinleştirildiğinde bir uyarı görüntülemek üzere yapılandırılırsa, raporda bir bilgi çubuğu görüntülenir.

 Çağrı Ağacı görünümündeki sütun tanımları hakkında daha fazla bilgi için aşağıdakilere bakın:

- [Çağrı Ağacı görünümü](../profiling/call-tree-view-sampling-data.md)

- [Çağrı Ağacı görünümü](../profiling/call-tree-view-instrumentation-data.md)

- [Çağrı Ağacı görünümü - örnekleme](../profiling/call-tree-view-dotnet-memory-sampling-data.md)

- [Çağrı Ağacı görünümü](../profiling/call-tree-view-contention-data.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Performans raporu görünümleri](../profiling/performance-report-views.md)
- [Enstrümantasyon veri değerlerini anlama](../profiling/understanding-instrumentation-data-values.md)
- [Örnekleme veri değerlerini anlama](../profiling/understanding-sampling-data-values.md)
