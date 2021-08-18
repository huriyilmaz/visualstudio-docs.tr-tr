---
description: Şu anda etkin olan tüm System. Threading. Tasks. TaskScheduler nesnelerinin dizisini alır.
title: GetTaskSchedulersForDebugger yöntemi | Microsoft Docs
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
ms.openlocfilehash: edcaa82677bf2b107c3a9dcc3f12ef9af05208be
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122153504"
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger Metodu
Şu anda etkin olan tüm nesnelerin bir dizisini alır <xref:System.Threading.Tasks.TaskScheduler> .

 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Bütünleştirilmiş kod:** mscorlib ( *mscorlib.dll*)

 bu iç üyeye .NET Framework erişeolmadığınızdan, ortak ara dil (cıl) içinde aşağıdaki sözdizimi sunulmaktadır.

## <a name="syntax"></a>Sözdizimi

```csharp
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed
```

## <a name="return-value"></a>Döndürülen değer
 <xref:System.Threading.Tasks.TaskScheduler>Bu, şu anda etkin olan tüm nesneler dizisi <xref:System.AppDomain> .

## <a name="remarks"></a>Açıklamalar
 Bu yöntem iş parçacığı açısından güvenli değildir ve diğer örnekleri ile aynı anda kullanmamalısınız <xref:System.Threading.Tasks.TaskScheduler> . Bu yöntemi hata ayıklayıcı 'dan yalnızca hata ayıklayıcı diğer tüm iş parçacıklarını askıya aldığı zaman çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [TaskScheduler sınıfı](../../extensibility/debugger/taskscheduler-class-internal-members.md)
