---
title: 'Nasıl Yapılır: Ek Enstrümantasyon Seçenekleri Belirt | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.advanced
helpviewer_keywords:
- instrumentation, options
- profiling tools, session options
- performance sessions, options
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2d1f7e912ed5960c52e3f0bfa40fe9b87e91a2e6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778706"
---
# <a name="how-to-specify-additional-instrumentation-options"></a>Nasıl yapılır: Ek izleme seçeneklerini belirtme

Visual Studio IDE'yi kullanarak veya komut satırı araçlarını kullanarak ikili araçlar alabilirsiniz. IDE içinden bir ikili enstrümanta, [VSInstr](../profiling/vsinstr.md) aracına ek enstrümantasyon seçenekleri belirterek enstrümantasyon sırasında toplanan verilerin hacmini kontrol edebilirsiniz. Bu seçenekler oturumda veya hedef düzeyde kullanılabilir. Örneğin, enstrümantasyon işlemi sırasında belirli işlevleri eklemek veya hariç tutmak için, hedef düzeyde ek enstrümantasyon seçeneğini kullanın.

> [!IMPORTANT]
> Eklenen her sonda, özgün programın davranışını biraz değiştirir. Bu değişiklik, analiz zamanında ek yükü neden olur. Bu ek yükün yaklaşık bir kısmı çıkarılmış olsa da, yine de çok iş parçacığı uygulamaları üzerinde ince zamanlama etkileri vardır. [VSInstr](../profiling/vsinstr.md) araç seçenekleri profil oluşturma sırasında veri toplamayı denetlemeye yardımcı olur.

## <a name="to-specify-additional-instrumentation-option"></a>Ek enstrümantasyon seçeneği belirtmek için

1. **Performans Gezgini'nde,** **Performans Oturumu'nu** seçin ve ardından sağ tıklatın ve **Özellikler'i**seçin.

2. Özellikler **Sayfalarında**Gelişmiş **özellikleri** tıklatın.

3. **Ek enstrümantasyon seçenekleri** kutusuna seçenekleri yazın.

     Örneğin, profil oluşturma düzeyini belirtmek için /CONTROL:THREAD'i kullanın. Seçeneklerin tam listesi için [VSInstr'a](../profiling/vsinstr.md)bakın.

4. **Tamam**'a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

[Performans oturumlarını](../profiling/configuring-performance-sessions.md)
yapılandırma[Komut satırından profil](../profiling/using-the-profiling-tools-from-the-command-line.md)
