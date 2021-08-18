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
ms.openlocfilehash: bd9f175a9d17475bc0d1346ef0f0b5367e33a411
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122141905"
---
# <a name="gpu-activity-graph"></a>GPU Etkinlik grafiği
Eşzamanlılık Görselleştiricisi'nde GPU Etkinliği grafiği, zaman içinde kullanımda olan DirectX altyapılarının sayısıyla ölçülen sistem üzerinde DirectX etkinliği düzeyini görüntüler.  Grafikte hangi altyapıların kullanılmış olduğu göster değil.  Herhangi bir GPU işi iş alıyorsa altyapının kullanımda olduğu kabul edilir.

## <a name="gpu-activity-graph-colors"></a>GPU Etkinliği grafı renkleri
 Yeşil, geçerli işlem tarafından DirectX Altyapılarının tüketimini gösterir.

 Açık gri, DirectX Altyapılarının sistem üzerinde diğer işlemler tarafından tüketimini gösterir. DirectX altyapılarının diğer işlemler tarafından tüketimini azaltmak için sistemde çalışan diğer işlemlerin sayısını azaltmanız gerekir.

 Beyaz, kullanılmayan DirectX altyapılarının sistemde kullanılabilir olduğunu gösterir. Bu altyapılardan yararlanmak için daha fazla fırsat bulursanız bu altyapılar süreciniz için kullanılabilir. Bazı altyapılar yalnızca belirli görev türleri için kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kullanım Görünümü](../profiling/utilization-view.md)