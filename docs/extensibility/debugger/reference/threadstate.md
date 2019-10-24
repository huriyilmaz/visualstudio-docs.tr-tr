---
title: THREADSTATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADSTATE
helpviewer_keywords:
- THREADSTATE enumeration
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d86baeeab046a7e605979d3af2d6329998f796ba
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727504"
---
# <a name="threadstate"></a>THREADSTATE
İş parçacığının durumunu belirtir.

## <a name="syntax"></a>Sözdizimi

```cpp
enum enum_THREADSTATE { 
   THREADSTATE_RUNNING = 0x0001,
   THREADSTATE_STOPPED = 0x0002,
   THREADSTATE_FRESH   = 0x0003,
   THREADSTATE_DEAD    = 0x0004,
   THREADSTATE_FROZEN  = 0x0005
};
typedef DWORD THREADSTATE;
```

```csharp
public enum enum_THREADSTATE { 
   THREADSTATE_RUNNING = 0x0001,
   THREADSTATE_STOPPED = 0x0002,
   THREADSTATE_FRESH   = 0x0003,
   THREADSTATE_DEAD    = 0x0004,
   THREADSTATE_FROZEN  = 0x0005
};
```

## <a name="fields"></a>Alanlar
 `THREADSTATE_RUNNING`\
 İş parçacığının çalıştığını gösterir.

 `THREADSTATE_STOPPED`\
 Bir kesme noktası nedeniyle iş parçacığının durdurulduğunu belirtir.

 `THREADSTATE_FRESH`\
 İş parçacığının oluşturulduğunu, ancak henüz kod çalışmadığını gösterir.

 `THREADSTATE_DEAD`\
 İş parçacığının ölü olduğunu gösterir.

 `THREADSTATE_FROZEN`\
 İş parçacığının dondurulmuş olduğunu belirtir (yürütme yapılamaz).

## <a name="remarks"></a>Açıklamalar
 [Threadproperties](../../../extensibility/debugger/reference/threadproperties.md) yapısının `dwThreadState` alanı için kullanılır.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft. VisualStudio. Debugger. Interop. dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sabit Listeleri](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)