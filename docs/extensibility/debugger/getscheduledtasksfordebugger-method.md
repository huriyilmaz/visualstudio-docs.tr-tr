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
ms.openlocfilehash: d25acf7d40c2f1f78dcf2102ca612289426c5f80
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073337"
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
