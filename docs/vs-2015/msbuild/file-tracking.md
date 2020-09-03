---
title: Dosya Izleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d8d999d65b207f72542b732842f6eb984df40764
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156465"
---
# <a name="file-tracking"></a>Dosya İzleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dosya izleme, bir işlem ve alt işlemleri için Windows dosya sistemine yapılan çağrıları kaydeder. Aşağıda listelenen işlevleri çağırarak, programlar bu oturum açma işleminin ne zaman açık ve kapalı olduğunu denetler ve kullanılacak günlük dosyasını belirtir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [EndTrackingContext](../msbuild/endtrackingcontext.md)  
 Geçerli bağlamı izlemeyi durdur.  
  
 [ResumeTracking](../msbuild/resumetracking.md)  
 [SuspendTracking](../msbuild/suspendtracking.md)çağrısından sonra izlemeyi sürdürür.  
  
 [SetThreadCount](../msbuild/setthreadcount.md)  
 İzleme için kullanılacak iş parçacığı sayısını ayarlayın.  
  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)  
 Yeni bir izleme bağlamı başlatın.  
  
 [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md)  
 Belirtilen köke sahip yeni bir izleme bağlamı başlatın.  
  
 [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md)  
 Son izleme ve sürüm kaynakları kullanıldı.  
  
 [SuspendTracking](../msbuild/suspendtracking.md)  
 İzlemeyi geçici olarak askıya alın.  
  
 [WriteAllTLogs](../msbuild/writealltlogs.md)  
 Tüm bağlamlar için izleme günlüklerini yazın.  
  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)  
 Geçerli bağlam için izleme günlüğünü yazın.
