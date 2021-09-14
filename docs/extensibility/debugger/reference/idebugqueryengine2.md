---
description: Bu arabirim, oturum hata ayıklama yöneticisinin (SDM) hata ayıklama altyapısını (DE) temsil eden bir arabirimi alamasına olanak sağlar.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725164"
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
Bu arabirim, oturum hata ayıklama yöneticisinin (SDM) hata ayıklama altyapısını (DE) temsil eden bir arabirimi alamasına olanak sağlar.

## <a name="syntax"></a>Syntax

```
IDebugQueryEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE, DE'nin kendi [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) arabirimine erişim izni vermek için en yaygın DE arabirimlerini [(IDebugProgram2,](../../../extensibility/debugger/reference/idebugprogram2.md) [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)ve [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)gibi) uygulayan nesnelere bu arabirimi uygulamaz.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi elde etmek için tipik bir DE arabiriminde [QueryInterface](/cpp/atl/queryinterface) çağrısı.

## <a name="methods-in-vtable-order"></a>VTable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugQueryEngine2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|Özel bir hata ayıklama altyapısı (DE) arabirimi alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim genellikle işlevlerde nedensellik sıralanmış adımlamayı desteklemek için [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) arabirimini uygulayan nesnede uygulanır; diğer bir ifadeyle, hata ayıklayıcı bir işlevden dışarı adımlarken, yürütülecek sonraki işlev yığında önceki işlev değil, tamamen başka bir iş parçacığında bir işlev olabilir. "Nedensellik" tanımı için hata [ayıklayıcısı sözlüğüne Visual Studio bakın.](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md)

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
