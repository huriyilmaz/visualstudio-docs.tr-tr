---
title: TaskScheduler Class - Dahili Üyeler | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a53abc8b24edb06445c23c19744d00d50de8735d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712575"
---
# <a name="taskscheduler-class---internal-members"></a>TaskScheduler Class - Dahili üyeler
Bu makalede, özel bir <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> hata ayıklama uygulamanıza yardımcı sınıfın iç üyeleri açıklanır. Bu sınıf hakkında genel bilgi <xref:System.Threading.Tasks.TaskScheduler> için başvuru makalesine bakın.

 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Montaj:** mscorlib *(mscorlib.dll*olarak)

 Bu dahili üyelere .NET Framework'den erişemediğinizden, aşağıdaki sözdizimi Ortak Ara Dil 'de (CIL) sağlanır.

## <a name="syntax"></a>Sözdizimi

```csharp
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler
       extends System.Object
```

## <a name="members"></a>Üyeler

### <a name="methods"></a>Yöntemler

|Adı|Açıklama|
|----------|-----------------|
|[GetScheduledTasksForDebugger](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|Zamanlanmış tüm görevlerin bir dizisini alır.|
|[GetTaskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|Şu anda etkin <xref:System.Threading.Tasks.TaskScheduler> olan tüm nesnelerin bir dizi alır.|

## <a name="remarks"></a>Açıklamalar

## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [.NET Framework için paralel uzantı dahili](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
