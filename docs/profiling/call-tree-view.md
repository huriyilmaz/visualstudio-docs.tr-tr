---
title: Çağrı ağacı görünümü | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74773341"
---
# <a name="call-tree-view"></a>Çağrı Ağacı görünümü
Çağrı ağacı görünümü, profili oluşturulmuş uygulamada geçen işlev yürütme yollarını görüntüler. Ağacın kökü, uygulamanın veya bileşenin giriş noktasıdır. Her işlev düğümü, çağırdığı tüm işlevleri ve bu işlev çağrıları hakkındaki performans verilerini listeler.

 Çağrı ağacı görünümü Ayrıca en çok kullanılan veya en sık örneklendiği bir işlevin yürütme yolunu genişletebilir ve vurgulayabilir. En yüksek performans maliyetli yolu göstermek için, işlevine sağ tıklayın ve ardından **etkin yolu genişlet**' e tıklayın.

 Profil oluşturma çalıştırmasında her işlem kök düğüm olarak görüntülenir. Başlangıç düğümü olarak ayarlamak istediğiniz düğüme sağ tıklayıp, ardından **kökü ayarla**' yı seçerek çağrı ağacı görünümünün başlangıç düğümünü ayarlayabilirsiniz.

 Kök düğümü ayarladığınızda, seçili düğümün alt ağacı hariç diğer tüm girişleri görünümden ortadan kaldırabilirsiniz. Kök düğümü, görüntülemekte olduğunuz düğüme geri sıfırlayabilirsiniz. Çağrı ağacı görünümü penceresinde, sağ tıklayın ve ardından **kökü Sıfırla**' yı seçin.

 Çağrı ağacı görünümü sütun eklemek veya kaldırmak için özelleştirilebilir. **Sütun adı başlık çubuğuna**sağ tıklayın ve ardından **sütun Ekle/Kaldır**' ı seçin.

 Çağrı ağacı görünümü, sunulan veri miktarını sınırlayarak gürültü azaltma için yapılandırılabilir. Gürültü azaltmasıyla, performans sorunları görünümde daha belirgin. Performans sorunlarının ayırt edilmesi kolay olduğunda, analiz daha kolay olur. Daha fazla bilgi için bkz. [nasıl yapılır: rapor görünümlerinde gürültü azaltılması yapılandırma](../profiling/how-to-configure-noise-reduction-in-report-views.md).

> [!NOTE]
> Gürültü azaltma etkinleştirildiğinde bir uyarı görüntüleyecek şekilde yapılandırıldıysa, raporda bir bilgi çubuğu görüntülenir.

 Çağrı ağacı görünümündeki sütunların tanımları hakkında daha fazla bilgi için aşağıdakilere bakın:

- [Çağrı ağacı görünümü](../profiling/call-tree-view-sampling-data.md)

- [Çağrı ağacı görünümü](../profiling/call-tree-view-instrumentation-data.md)

- [Çağrı ağacı görünümü-örnekleme](../profiling/call-tree-view-dotnet-memory-sampling-data.md)

- [Çağrı ağacı görünümü](../profiling/call-tree-view-contention-data.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Performans raporu görünümleri](../profiling/performance-report-views.md)
- [İzleme veri değerlerini anlama](../profiling/understanding-instrumentation-data-values.md)
- [Örnekleme veri değerlerini anlama](../profiling/understanding-sampling-data-values.md)
