---
title: GPU Etkinlik Graph | Microsoft Docs
description: Eşzamanlılık Görselleştiricisi'nde sistem üzerinde DirectX etkinliği düzeyini gösteren GPU Etkinliği grafiğini anlıyoruz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 1a2410ddbeb365cb908c5718b3800f41f8eb28997ed3e22ccbf63589c601e0b0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121368597"
---
# <a name="gpu-activity-graph"></a>GPU Etkinlik grafiği
Eşzamanlılık Görselleştiricisi'nde GPU Etkinliği grafiği, zaman içinde kullanımda olan DirectX altyapılarının sayısıyla ölçülen sistem üzerinde DirectX etkinliği düzeyini görüntüler.  Grafikte hangi altyapıların kullanılmış olduğu göster değil.  Herhangi bir GPU işi iş alıyorsa altyapının kullanımda olduğu kabul edilir.

## <a name="gpu-activity-graph-colors"></a>GPU Etkinliği grafı renkleri
 Yeşil, geçerli işlem tarafından DirectX Altyapılarının tüketimini gösterir.

 Açık gri, DirectX Altyapılarının sistem üzerinde diğer işlemler tarafından tüketimini gösterir. DirectX altyapılarının diğer işlemler tarafından tüketimini azaltmak için sistemde çalışan diğer işlemlerin sayısını azaltmanız gerekir.

 Beyaz, kullanılmayan DirectX altyapılarının sistemde kullanılabilir olduğunu gösterir. Bu altyapılardan yararlanmak için daha fazla fırsat bulursanız bu altyapılar süreciniz için kullanılabilir. Bazı altyapılar yalnızca belirli görev türleri için kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kullanım Görünümü](../profiling/utilization-view.md)