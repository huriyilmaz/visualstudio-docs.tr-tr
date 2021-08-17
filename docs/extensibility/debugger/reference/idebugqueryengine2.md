---
description: Bu arabirim, oturum hata ayıklama Yöneticisi 'nin (SDM) hata ayıklama altyapısını (DE) temsil eden bir arabirim almasına izin verir.
title: IDebugQueryEngine2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: bf399a8ccf018e8e18c18ba0af2b54a0e5b948c9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122029872"
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
Bu arabirim, oturum hata ayıklama Yöneticisi 'nin (SDM) hata ayıklama altyapısını (DE) temsil eden bir arabirim almasına izin verir.

## <a name="syntax"></a>Syntax

```
IDebugQueryEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Ayrıca, bu arabirimi en yaygın olarak kullanılan ( [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md), [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)ve [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)gibi) nesnelerin kendi [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) arabirimine erişime izin vermek için uygulayan nesneler üzerinde de uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi edinmek için tipik bir DE arabirimi üzerinde [QueryInterface](/cpp/atl/queryinterface) 'i çağırın.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugQueryEngine2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|Özel bir hata ayıklama altyapısı (DE) arabirimini alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim tipik olarak işlevler aracılığıyla sıralı adımlamayı desteklemek için [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) arabirimini uygulayan nesnede uygulanır; diğer bir deyişle, hata ayıklayıcı bir işlevden dışarı adımla, yürütülecek sonraki işlev yığında önceki işlev olmayabilir, ancak başka bir iş parçacığında bir işlev değildir. "causitesi" tanımı için bkz. [Visual Studio hata ayıklayıcı sözlüğü](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md).

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
