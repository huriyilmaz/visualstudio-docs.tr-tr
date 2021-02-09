---
title: IDebugProviderProgramNode2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2
helpviewer_keywords:
- IDebugProviderProgramNode2
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e11472c2c883705c36ab71a37b1af10eb1cb5b10
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909820"
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
 Bu arabirim, hata ayıklanan programdan ayrı bir işlem alanında çalıştığında uygulanır: Örneğin, hata ayıklanan programın işlem alanı yerine Visual Studio işlem alanında çalışır.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
