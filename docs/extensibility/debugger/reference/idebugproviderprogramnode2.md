---
description: Bu arabirim, programla ilgili arabirimleri işlem sınırları arasında sıralar.
title: IDebugProviderProgramNode2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2
helpviewer_keywords:
- IDebugProviderProgramNode2
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 43a66e927d2a1d2e1afc84688bb3a36451fffecc
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725166"
---
# <a name="idebugproviderprogramnode2"></a>IDebugProviderProgramNode2
Bu arabirim, programla ilgili arabirimleri işlem sınırları arasında sıralar.

## <a name="syntax"></a>Syntax

```
IDebugProviderProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Hata ayıklama altyapısı (DE), bu arabirimi işlem sınırları genelinde sıralama arabirimlerini desteklemek için [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) uygulayan aynı nesne üzerinde uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [](/cpp/atl/queryinterface) `IDebugProgramNode2` Bu arabirimi edinmek Için arabirim üzerinde QueryInterface 'i çağırın. Bu arabirim alınamıyorsa, DE arabirimlerin sıralamasını desteklemez.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Bu arabirim aşağıdaki yöntemi uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|İşlem sınırları genelinde belirtilen bir arabirimi alır.|

## <a name="remarks"></a>Açıklamalar
 bu arabirim, hata ayıklanan programdan ayrı bir işlem alanında çalıştığında uygulanır: örneğin, hata ayıklanan programın işlem alanı yerine Visual Studio işlem alanında çalışır.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
