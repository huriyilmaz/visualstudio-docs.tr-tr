---
title: IDebugQueryEngine2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31b1784055c54c9243237c81edb708e13de9bc5b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720658"
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
Bu arabirim, oturum hata ayıklama yöneticisinin (SDM) hata ayıklama altyapısını (DE) temsil eden bir arabirimi almasına olanak tanır.

## <a name="syntax"></a>Sözdizimi

```
IDebugQueryEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE, DE'nin kendisinin [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) arabirimine erişime izin vermek için en yaygın DE arabirimlerini [(IDebugProgram2,](../../../extensibility/debugger/reference/idebugprogram2.md) [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)ve [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)gibi) uygulayan nesnelerüzerinde bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi elde etmek için normal bir DE arabiriminde [QueryInterface'i](/cpp/atl/queryinterface) arayın.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugQueryEngine2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|Özel hata ayıklama altyapısı (DE) arabirimi alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim genellikle işlevler arasında nedensellik sıralı adımlama desteklemek için [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) arabirimini uygulayan nesnede uygulanır; diğer bir deyişle, hata ayıklayıcı bir işlevin dışına adım atıldığında, yürütülecek sonraki işlev yığındaki önceki işlev değil, tamamen başka bir iş parçacığındaki işlev olabilir. "Nedensellik" tanımı için Visual [Studio Debugger Sözlüğü'ne](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md)bakın.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
