---
title: GetTaskSchedulersForDebugger Yöntemi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a3b0c8c16b10a4cf2268161d8a2db96c10303b1c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738651"
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger Metodu
Şu anda etkin <xref:System.Threading.Tasks.TaskScheduler> olan tüm nesnelerin bir dizi alır.

 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Montaj:** mscorlib *(mscorlib.dll*olarak)

 Bu iç üyeye .NET Framework'den erişemediğinizden, aşağıdaki sözdizimi Ortak Ara Dil 'de (CIL) sağlanır.

## <a name="syntax"></a>Sözdizimi

```csharp
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed
```

## <a name="return-value"></a>Döndürülen değer
 Şu anda <xref:System.Threading.Tasks.TaskScheduler> etkin <xref:System.AppDomain>olan tüm nesnelerin bir dizi.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem iş parçacığı güvenli değildir ve diğer örnekleri ile <xref:System.Threading.Tasks.TaskScheduler>aynı anda kullanmamalısınız. Hata ayıklama diğer tüm iş parçacığı askıya aldığında bu yöntemi bir hata ayıklama dan çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [TaskScheduler sınıfı](../../extensibility/debugger/taskscheduler-class-internal-members.md)
