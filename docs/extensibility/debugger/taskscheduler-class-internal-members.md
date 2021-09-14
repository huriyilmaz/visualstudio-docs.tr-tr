---
title: TaskScheduler sınıfı-Iç Üyeler | Microsoft Docs
description: Özel bir hata ayıklayıcı uygulamanıza yardımcı olan System. Threading. Tasks. TaskScheduler sınıfının iç üyeleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 02897900a9117eee3d9a917b2e86580d21980345
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626372"
---
# <a name="taskscheduler-class---internal-members"></a>TaskScheduler sınıfı-Iç Üyeler
Bu makale, <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> özel bir hata ayıklayıcı uygulamanıza yardımcı olan sınıfın iç üyelerini açıklar. Bu sınıf hakkında genel bilgi için <xref:System.Threading.Tasks.TaskScheduler> başvuru makalesine bakın.

 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Bütünleştirilmiş kod:** mscorlib ( *mscorlib.dll*)

 bu iç üyelere .NET Framework erişemediği için, ortak ara dil (cıl) içinde aşağıdaki sözdizimi sunulmaktadır.

## <a name="syntax"></a>Syntax

```csharp
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler
       extends System.Object
```

## <a name="members"></a>Üyeler

### <a name="methods"></a>Yöntemler

|Ad|Açıklama|
|----------|-----------------|
|[GetScheduledTasksForDebugger](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|Tüm zamanlanmış görevlerin bir dizisini alır.|
|[GetTaskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|Şu anda etkin olan tüm nesnelerin bir dizisini alır <xref:System.Threading.Tasks.TaskScheduler> .|

## <a name="remarks"></a>Açıklamalar

## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [.NET Framework için paralel uzantı iç işlevleri](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
