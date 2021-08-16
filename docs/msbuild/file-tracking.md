---
title: Dosya Izleme | Microsoft Docs
description: bir işlem ve onun alt işlemleri için Windows dosya sistemine yapılan çağrıları günlüğe kaydetmek için MSBuild dosya izleme işlevlerini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: fbff31884c3aa6539b286772f1517b1594462579a5992f8fa750a8e5b7b03729
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121428087"
---
# <a name="file-tracking"></a>Dosya izleme

dosya izleme, bir işlem ve alt işlemleri için Windows dosya sistemine çağrı kaydeder. Aşağıda listelenen işlevleri çağırarak, programlar bu oturum açma işleminin ne zaman açık ve kapalı olduğunu denetler ve kullanılacak günlük dosyasını belirtir.

- [EndTrackingContext](../msbuild/endtrackingcontext.md) Geçerli bağlamı izlemeyi durdur.

- [ResumeTracking](../msbuild/resumetracking.md) [SuspendTracking](../msbuild/suspendtracking.md)çağrısından sonra izlemeyi sürdürür.

- [SetThreadCount](../msbuild/setthreadcount.md) İzleme için kullanılacak iş parçacığı sayısını ayarlayın.

- [StartTrackingContext](../msbuild/starttrackingcontext.md) Yeni bir izleme bağlamı başlatın.

- [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md) Belirtilen köke sahip yeni bir izleme bağlamı başlatın.

- [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md) Son izleme ve sürüm kaynakları kullanıldı.

- [SuspendTracking](../msbuild/suspendtracking.md) İzlemeyi geçici olarak askıya alın.

- [WriteAllTLogs](../msbuild/writealltlogs.md) Tüm bağlamlar için izleme günlüklerini yazın.

- [WriteContextTLogs](../msbuild/writecontexttlogs.md) Geçerli bağlam için izleme günlüğünü yazın.
