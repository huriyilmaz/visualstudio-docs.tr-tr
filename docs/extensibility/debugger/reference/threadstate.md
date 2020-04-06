---
title: THREADSTATE | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADSTATE
helpviewer_keywords:
- THREADSTATE enumeration
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1b291cc1668b2b867729da11d4c561f74567f257
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713332"
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
 Bir kesme noktası nedeniyle iş parçacığının durdurulduğunu gösterir.

 `THREADSTATE_FRESH`\
 İş parçacığının oluşturulduğunu, ancak henüz kod çalıştırmadığını gösterir.

 `THREADSTATE_DEAD`\
 İş parçacığının öldüğünü gösterir.

 `THREADSTATE_FROZEN`\
 İş parçacığının dondurulduğunu gösterir (yürütme yapılamaz).

## <a name="remarks"></a>Açıklamalar
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) `dwThreadState` yapısının alanı için kullanılır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
