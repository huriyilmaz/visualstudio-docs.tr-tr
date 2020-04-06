---
title: GetScheduledTasksForDebugger Yöntemi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fca6c8e92cd0b4755bd79b8e142a7e1d283f868d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738656"
---
# <a name="getscheduledtasksfordebugger-method"></a>GetScheduledTasksForDebugger Metodu
Zamanlanmış tüm görevlerin bir dizisini alır.

 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Montaj:** mscorlib *(mscorlib.dll*olarak)

 Bu iç üyeye .NET Framework'den erişemediğinizden, aşağıdaki sözdizimi Ortak Ara Dil 'de (CIL) sağlanır.

## <a name="syntax"></a>Sözdizimi

```csharp
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed
```

## <a name="return-value"></a>Dönüş Değeri
 Tüm zamanlanmış görevler dizisi. Her görev yürütülen veya yürütmeyi tamamladı.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem iş parçacığı güvenli değildir ve diğer örnekleri ile <xref:System.Threading.Tasks.TaskScheduler>aynı anda kullanmamalısınız. Hata ayıklama diğer tüm iş parçacığı askıya aldığında bu yöntemi bir hata ayıklama dan çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [TaskScheduler sınıfı](../../extensibility/debugger/taskscheduler-class-internal-members.md)
