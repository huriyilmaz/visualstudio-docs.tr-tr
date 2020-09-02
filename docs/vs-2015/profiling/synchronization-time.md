---
title: Eşitleme saati | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.synchronization
helpviewer_keywords:
- Concurrency Visualizer, Synchronization Time
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 218f333f97e8252993f87893238a0f51f964d6c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151393"
---
# <a name="synchronization-time"></a>Eşitleme Zamanı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zaman çizelgesindeki bu segmentler, eşitleme olarak kategorilere ayrılan engelleyici sürelerle ilişkilendirilir. Bir iş parçacığı eşitlemede engellenmiş olarak işaretlendiğinde, bunlardan biri kapsanır:  
  
- İş parçacığının yürütülmesi, veya gibi iyi bilinen bir iş parçacığı eşitleme API 'sine çağrı ile sonuçlanmasına neden olmuş olabilir `EnterCriticalSection()` `WaitForSingleObject()` .  
  
- API eşleştirme algoritması tamamen kapsamlı olamaz ve bu nedenle, çağrı yığınında bir çerçeve bu kategoriye eşlenmiş temel bir çekirdek engelleme temel değerine ulaştığından, diğer kategorilere eşlenebilen bazı API 'Ler eşitleme olarak da görünebilir.  
  
  Bir iş parçacığı engelleme olayının temel nedenini anlamak için engelleme çağrı yığınlarını ve profil raporlarını dikkatle inceleyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)
