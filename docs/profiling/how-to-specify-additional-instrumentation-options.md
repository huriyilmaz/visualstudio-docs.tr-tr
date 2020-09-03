---
title: Nasıl yapılır-ek Izleme seçenekleri belirtme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 8390c4aab0624aa59f62397e0b41bcbcc1c80cdd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85331985"
---
# <a name="how-to-specify-additional-instrumentation-options"></a>Nasıl yapılır: Ek izleme seçeneklerini belirtme

Visual Studio IDE 'yi kullanarak veya komut satırı araçlarını kullanarak ikili dosyaları seçebilirsiniz. IDE içinden bir ikili değer verirseniz, [vsinstr](../profiling/vsinstr.md) aracına ek izleme seçenekleri belirterek, izleme sırasında toplanan veri hacminin denetimini yapabilirsiniz. Bu seçenekler oturumda veya hedef düzeyinde kullanılabilir. Örneğin, izleme işlemi sırasında belirli işlevleri dahil etmek veya hariç tutmak için, hedef düzeyinde ek izleme seçeneğini kullanın.

> [!IMPORTANT]
> Eklenen her araştırma, özgün programın davranışını biraz değiştirir. Bu değişiklik çözümleme sırasında ek yüke neden olur. Bu ek yükün yaklaşık bir nedeni kaldırılmış olsa da, çok iş parçacıklı uygulamalar üzerinde hala hafif zamanlama etkileri vardır. [Vsinstr](../profiling/vsinstr.md) aracı seçenekleri, profil oluşturma sırasında veri toplamayı denetlemenize yardımcı olur.

## <a name="to-specify-additional-instrumentation-option"></a>Ek izleme seçeneğini belirtmek için

1. **Performans Gezgini**' de, **performans oturumu** ' nu seçin ve ardından sağ tıklayıp **Özellikler**' i seçin.

2. **Özellikler sayfalarında** **Gelişmiş** Özellikler ' e tıklayın.

3. **Ek izleme seçenekleri** kutusunda seçenekler yazın.

     Örneğin, profil oluşturma düzeyini belirtmek için/CONTROL: THREAD komutunu kullanın. Seçeneklerin tamamı listesi için bkz. [vsinstr](../profiling/vsinstr.md).

4. **Tamam**’a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

[Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md) 
 [Komut satırından profil](../profiling/using-the-profiling-tools-from-the-command-line.md)
