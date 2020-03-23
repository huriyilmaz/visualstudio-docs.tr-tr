---
title: Dosya Takibi | Microsoft Dokümanlar
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
ms.openlocfilehash: 9335ca6608d36edbd17e47a441e13aecaa41c890
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634207"
---
# <a name="file-tracking"></a>Dosya izleme

Dosya izleme günlükleri, bir işlem ve alt işlemleri için Windows dosya sistemine çağrılar. Aşağıda listelenen işlevleri arayarak, programlar bu günlüğe kaydetmeve kapatmayı ne zaman kullanacağını denetler ve kullanılacak günlük dosyasını belirtir.

- [EndTrackingBağlam](../msbuild/endtrackingcontext.md) Geçerli bağlamı izlemeyi durdurun.

- [Özgeçmiş Takibi](../msbuild/resumetracking.md) [SuspendTracking](../msbuild/suspendtracking.md)için bir aramadan sonra izleme devam edin.

- [SetThreadCount](../msbuild/setthreadcount.md) İzleme için kullanılacak iş parçacığı sayısını ayarlayın.

- [Başlangıç İzleme Bağlamı](../msbuild/starttrackingcontext.md) Yeni bir izleme bağlamı başlatın.

- [Başlangıç İzlemeBağlamWithroot](../msbuild/starttrackingcontextwithroot.md) Belirtilen bir kökle yeni bir izleme bağlamı başlatın.

- [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md) Kullanılan izleme ve serbest bırakma kaynaklarını sonla.

- [Askıya Alma İzleme](../msbuild/suspendtracking.md) İzlemeyi geçici olarak askıya alın.

- [WriteAllTLogs](../msbuild/writealltlogs.md) Tüm bağlamlar için izleme günlüklerini yazın.

- [YazmaContextTLogs](../msbuild/writecontexttlogs.md) Geçerli bağlam için izleme günlüğünü yazın.
