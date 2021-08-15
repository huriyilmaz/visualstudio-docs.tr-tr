---
description: Tüm zamanlanmış görevlerin bir dizisini alır.
title: GetScheduledTasksForDebugger yöntemi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: e63c7fefe387c0bd7980980eb43a0f78b5c4ffb5a878af3d22b16b4f77806ba7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121342745"
---
# <a name="getscheduledtasksfordebugger-method"></a>GetScheduledTasksForDebugger Metodu
Tüm zamanlanmış görevlerin bir dizisini alır.

 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Bütünleştirilmiş kod:** mscorlib ( *mscorlib.dll*)

 bu iç üyeye .NET Framework erişeolmadığınızdan, ortak ara dil (cıl) içinde aşağıdaki sözdizimi sunulmaktadır.

## <a name="syntax"></a>Syntax

```csharp
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed
```

## <a name="return-value"></a>Dönüş Değeri
 Zamanlanan tüm görevlerin dizisi. Her görev yürütülüyor veya yürütmeyi bitirdi.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem iş parçacığı açısından güvenli değildir ve diğer örnekleri ile aynı anda kullanmamalısınız <xref:System.Threading.Tasks.TaskScheduler> . Bu yöntemi hata ayıklayıcı 'dan yalnızca hata ayıklayıcı diğer tüm iş parçacıklarını askıya aldığı zaman çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [TaskScheduler sınıfı](../../extensibility/debugger/taskscheduler-class-internal-members.md)
