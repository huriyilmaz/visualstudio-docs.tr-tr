---
title: CPU Kullanımı Graph | Microsoft Docs
description: Bir uygulamanın zaman içinde kullanım düzeyini gösteren CPU Kullanımı grafı hakkında bilgi edinebilirsiniz. Kullanım, kullanımda mantıksal çekirdek sayısı olarak gösterilir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph
helpviewer_keywords:
- CPU Utilization GraphConcurrency Visualizer, CPU Utilization Graph
ms.assetid: 5332fd38-622d-47a3-874f-8c2fd7a30f95
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 758c90c3cdf5c458fc355f9f6eaf9c7233bd3cb4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122039195"
---
# <a name="cpu-utilization-graph"></a>CPU Kullanımı grafiği
CPU Kullanımı grafı, bir uygulamanın zaman içinde kullanım düzeyini gösterir. X ekseni izlemenin süresini, y ekseni ise sistem üzerinde mantıksal çekirdek sayısını temsil eder. Grafik belirli bir zamanda hangi çekirdeğin etkin olduğunu göstermez. Örneğin, her biri belirli bir süre için yüzde 50 kapasitede çalışan iki çekirdek varsa, bu görünümde bir mantıksal çekirdek kullanılır.

## <a name="cpu-utilization-graph-colors"></a>CPU Kullanımı graf renkleri

- Yeşil, geçerli işlem tarafından sistemdeki mantıksal çekirdeklerin kullanımını gösterir.

- Açık gri, sistemdeki diğer işlemler tarafından mantıksal çekirdeklerin kullanımını gösterir. CPU grafı içinde açık grinin yüksek bir yüzdesi, sistemin diğer işlemler tarafından yoğun bir şekilde yükleniyor olduğunu ve işleminizin büyük olasılıkla onlar tarafından önek olacağını gösterir. Mantıksal çekirdeklerin diğer işlemler tarafından tüketimini azaltmak için sistemde çalıştır çalıştırılalarının sayısını azalt.

- Koyu gri, sistem işlemi tarafından mantıksal çekirdeklerin tüketimini gösterir. Bunu doğrudan kontrol etmek doğru değildir, ancak ne zaman oluştuğunu bilmek yararlı olur çünkü bu işlem süreciniz için mantıksal çekirdeklerin kullanılabilirliğini etkileyebilir.

- Beyaz, sistem üzerinde kullanılmayan mantıksal çekirdeklerin kullanılabilirliğini gösterir. Paralellik için daha fazla fırsat bulursanız bu çekirdekler süreciniz için kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kullanım Görünümü](../profiling/utilization-view.md)
- [Ortalama CPU Kullanımı](../profiling/average-cpu-utilization.md)