---
title: CPU kullanım grafiği | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph
helpviewer_keywords:
- CPU Utilization GraphConcurrency Visualizer, CPU Utilization Graph
ms.assetid: 5332fd38-622d-47a3-874f-8c2fd7a30f95
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8058995c8ae45c40f202aaa1e788891da3eb985d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180495"
---
# <a name="cpu-utilization-graph"></a>CPU Kullanım Grafiği
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

CPU kullanım grafiğinde, zaman içinde bir uygulamadaki kullanım düzeyi gösterilir. X ekseni, izlemenin süresini temsil eder ve y ekseni, sistemdeki mantıksal çekirdek sayısını temsil eder. Grafik, belirli bir zamanda hangi belirli çekirdeğin etkin olduğunu göstermez. Örneğin, belirli bir süre boyunca her biri yüzde 50 kapasiteye iki çekirdek çalışıyorsa, bu görünüm kullanılan bir mantıksal çekirdeği gösterir.  
  
## <a name="cpu-utilization-graph-colors"></a>CPU kullanımı grafik renkleri  
  
- Yeşil, geçerli işlem tarafından sistemdeki mantıksal çekirdekler kullanımını gösterir.  
  
- Açık gri, sistemdeki diğer işlemlere göre mantıksal çekirdekler kullanımını gösterir. CPU grafiğinde yüksek oranda açık gri yüzdesi, sistemin diğer işlemler tarafından yoğun bir şekilde yüklendiğini ve işleminizin kendileri tarafından önceden gerçekleşme olasılığı olduğunu gösterir. Mantıksal çekirdekleri diğer işlemlere göre tüketimini azaltmak için, sistemde çalışan bunların sayısını azaltın.  
  
- Koyu gri, mantıksal çekirdekler tarafından sistem işleminin tüketimini gösterir. Bunu doğrudan denetleyemiyorsunuz, ancak işlemin ne zaman meydana geldiğini bilmeniz yararlı olur, çünkü işlem için mantıksal çekirdekler kullanılabilirliğini etkileyebilir.  
  
- Beyaz, sistemdeki kullanılmayan mantıksal çekirdekler için kullanılabilirliği gösterir. Paralellik için daha fazla fırsat bulabiliyorsanız, bu çekirdekler işleminiz için kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kullanım görünümü](../profiling/utilization-view.md)   
 [Ortalama CPU Kullanımı](../profiling/average-cpu-utilization.md)
