---
description: İş parçacığının durumunu belirtir.
title: THREADSTATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADSTATE
helpviewer_keywords:
- THREADSTATE enumeration
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e4aa5162259cf1937ef24506a32be9d87fb61327
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634729"
---
# <a name="threadstate"></a>THREADSTATE
İş parçacığının durumunu belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_THREADSTATE { 
   THREADSTATE_RUNNING = 0x0001,
   THREADSTATE_STOPPED = 0x0002,
   THREADSTATE_FRESH   = 0x0003,
   THREADSTATE_DEAD    = 0x0004,
   THREADSTATE_FROZEN  = 0x0005
};
typedef DWORD THREADSTATE;
```

```csharp
public enum enum_THREADSTATE { 
   THREADSTATE_RUNNING = 0x0001,
   THREADSTATE_STOPPED = 0x0002,
   THREADSTATE_FRESH   = 0x0003,
   THREADSTATE_DEAD    = 0x0004,
   THREADSTATE_FROZEN  = 0x0005
};
```

## <a name="fields"></a>Alanlar
 `THREADSTATE_RUNNING`\
 İş parçacığının çalışıyor olduğunu gösterir.

 `THREADSTATE_STOPPED`\
 Bir kesme noktası nedeniyle iş parçacığının durdurulmuş olduğunu gösterir.

 `THREADSTATE_FRESH`\
 İş parçacığının oluşturulmuş olduğunu ancak henüz kod çalıştırmamış olduğunu gösterir.

 `THREADSTATE_DEAD`\
 İş parçacığının yok olduğunu gösterir.

 `THREADSTATE_FROZEN`\
 İş parçacığının dondurulup dondurulup gerçekleştirile olmadığını gösterir.

## <a name="remarks"></a>Açıklamalar
 `dwThreadState` [THREADPROPERTIES yapısının alanı için](../../../extensibility/debugger/reference/threadproperties.md) kullanılır.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
