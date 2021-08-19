---
description: Bu bekleyen kesme noktasını bir veya daha fazla kod konumuna bağlar.
title: 'IDebugPendingBreakpoint2:: bind | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::Bind
helpviewer_keywords:
- Bind method
- IDebugPendingBreakpoint2::Bind method
ms.assetid: 46e3f307-219d-40cd-a929-d41399c60ecf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 53522a69392f52eaea2311da49ab88679a39990a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160107"
---
# <a name="idebugpendingbreakpoint2bind"></a>IDebugPendingBreakpoint2::Bind
Bu bekleyen kesme noktasını bir veya daha fazla kod konumuna bağlar.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Bind( 
   void 
);
```

```csharp
int Bind();
```

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. `E_BP_DELETED`Kesme noktasının silinip silinmediğini döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem çağrıldığında, bir hata ayıklama altyapısı (DE), bu bekleyen kesme noktasını eşleşen tüm kod konumlarına bağlamayı denemelidir.

 Bu yöntem çağrıldıktan sonra, [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) veya [enumerrorbreakpoint](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)çağrılarına çağrı yapmadan önce çağıranın, bekleyen kesme noktasının bağlandığını veya hata olduğunu belirten olayları beklemesi gerekir. Yöntemler sırasıyla tüm bağlantılı veya hata kesme noktalarını numaralandıracaktır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)
- [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
