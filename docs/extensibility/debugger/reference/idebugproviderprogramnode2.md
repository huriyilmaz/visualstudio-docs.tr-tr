---
title: IDebugProviderProgramNode2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2
helpviewer_keywords:
- IDebugProviderProgramNode2
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 815a945f6fb591960ebf0bf4b4fcd9d842ffefd3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720686"
---
# <a name="idebugproviderprogramnode2"></a>IDebugProviderProgramNode2
Bu arabirim, programla ilgili arabirimleri işlem sınırları boyunca yönlendirir.

## <a name="syntax"></a>Sözdizimi

```
IDebugProviderProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE), bu arabirimi, işlem sınırları içinde bağlantı arabirimlerini desteklemek için [IDebugProgramNode2'yi](../../../extensibility/debugger/reference/idebugprogramnode2.md) uygulayan nesne üzerinde uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi `IDebugProgramNode2` elde etmek için [queryinterface'i](/cpp/atl/queryinterface) bir arabirimden arayın. Bu arabirim elde edilemiyorsa, DE arabirimlerin mareşaling desteklemez.

## <a name="methods-in-vtable-order"></a>Vtable sırasına göre yöntemler
 Bu arabirim aşağıdaki yöntemi uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|İşlem sınırları arasında belirli bir arabirim alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim, DE, debugged olan programdan ayrı bir işlem alanında çalıştığında uygulanır: örneğin, DE, programın debugged işlem alanı yerine Visual Studio işlem alanında çalışırken.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
