---
title: Dosya Izleme | Microsoft Docs
description: Bir işlem ve alt işlemleri için Windows dosya sistemi çağrılarını günlüğe kaydetmek için MSBuild dosya izleme işlevlerini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d61c3478515f2c8fa867666e6ff4ff72a0d4e65b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877128"
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
