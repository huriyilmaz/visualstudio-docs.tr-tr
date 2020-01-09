---
title: Dosya Izleme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ee4620e845205a936bbdf48a9872c4dec3305ea
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596040"
---
# <a name="file-tracking"></a>Dosya izleme
Dosya izleme, bir işlem ve alt işlemleri için Windows dosya sistemine yapılan çağrıları kaydeder. Aşağıda listelenen işlevleri çağırarak, programlar bu oturum açma işleminin ne zaman açık ve kapalı olduğunu denetler ve kullanılacak günlük dosyasını belirtir.

- [EndTrackingContext](../msbuild/endtrackingcontext.md) Geçerli bağlamı izlemeyi durdur.

- [ResumeTracking](../msbuild/resumetracking.md) [SuspendTracking](../msbuild/suspendtracking.md)çağrısından sonra izlemeyi sürdürür.

- [SetThreadCount](../msbuild/setthreadcount.md) İzleme için kullanılacak iş parçacığı sayısını ayarlayın.

- [StartTrackingContext](../msbuild/starttrackingcontext.md) Yeni bir izleme bağlamı başlatın.

- [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md) Belirtilen köke sahip yeni bir izleme bağlamı başlatın.

- [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md) Son izleme ve sürüm kaynakları kullanıldı.

- [SuspendTracking](../msbuild/suspendtracking.md) İzlemeyi geçici olarak askıya alın.

- [WriteAllTLogs](../msbuild/writealltlogs.md) Tüm bağlamlar için izleme günlüklerini yazın.

- [WriteContextTLogs](../msbuild/writecontexttlogs.md) Geçerli bağlam için izleme günlüğünü yazın.
