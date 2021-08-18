---
title: Bellek Yönetimi Süresi | Microsoft Docs
description: Bu senaryonun, bir iş parçacığının Disk Belleği gibi bir bellek yönetimi işlemiyle ilişkili bir olay tarafından engellenmiş olduğunu nasıl ifade ettiği hakkında bilgi edinmek.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.paging
helpviewer_keywords:
- Concurrency Visualizer, Paging Time
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ed5483c89e9435d5bd0712ef562e80fde2c73e26
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122054541"
---
# <a name="memory-management-time"></a>Bellek yönetim süresi
Zaman çizelgesinde yer alan bu segmentler, Bellek Yönetimi olarak kategorilere ayrılmış engelleme süreleri ile ilişkilendirilmektedir. Bu senaryo, bir iş parçacığının Disk Belleği gibi bir bellek yönetimi işlemiyle ilişkili bir olay tarafından engellenmiş olduğunu gösterir. Bu süre boyunca, Eşzamanlılık Görselleştiricisi'nin bellek yönetimi olarak sayıyor olduğu bir API'de veya çekirdek durumda bir iş parçacığı engellendi. Bunlar disk belleği ve bellek ayırma gibi olayları içerir.

 Bellek Yönetimi olarak kategorilere ayrılmış blokların temel nedenlerini daha iyi anlamak için ilişkili çağrı yığınlarını ve profil raporlarını inceleme.

## <a name="see-also"></a>Ayrıca bkz.
- [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)