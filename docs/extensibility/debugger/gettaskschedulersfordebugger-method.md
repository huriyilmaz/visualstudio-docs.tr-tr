---
description: Şu anda etkin olan tüm System.Threading.Tasks.TaskScheduler nesnelerini içeren bir diziyi döndürür.
title: GetTaskSchedulersForDebugger Metodu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 04cc9a685554971e4e4065dba95bb1ac3118f56d470c82da474fe8349769c8dd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121417801"
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger Metodu
Şu anda etkin olan tüm <xref:System.Threading.Tasks.TaskScheduler> nesnelerin dizisini döndürür.

 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Derleme:** mscorlib *(mscorlib.dll*)

 Bu iç üyeye .NET Framework erişe .NET Framework Ortak Ara Dil (CIL) içinde sağlanmıştır.

## <a name="syntax"></a>Sözdizimi

```csharp
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed
```

## <a name="return-value"></a>Döndürülen değer
 Şu anda bu <xref:System.Threading.Tasks.TaskScheduler> içinde etkin olan tüm nesnelerin <xref:System.AppDomain> dizisi.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem iş parçacığı güvenli değildir ve bunu diğer örnekleriyle eşzamanlı olarak kullanmamalı. <xref:System.Threading.Tasks.TaskScheduler> Bu yöntemi yalnızca hata ayıklayıcı diğer tüm iş parçacıklarını askıya alınmış olduğunda bir hata ayıklayıcısından çağır.

## <a name="see-also"></a>Ayrıca bkz.
- [TaskScheduler sınıfı](../../extensibility/debugger/taskscheduler-class-internal-members.md)
