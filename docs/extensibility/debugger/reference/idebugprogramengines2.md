---
title: IDebugProgramEngines2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2
helpviewer_keywords:
- IDebugProgramEngines2 interface
ms.assetid: 53d648f0-6c11-4337-badd-c43f3872b62c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 56c74b265331b67564856baa003632d8d778bfb3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898899"
---
# <a name="idebugprogramengines2"></a>IDebugProgramEngines2
Bu arabirim program düğümleri tarafından, bu programda hata ayıklayacakları tüm olası hata ayıklama altyapılarını (DE) belirtmek için kullanılır.

## <a name="syntax"></a>Syntax

```
IDebugProgramEngines2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bir DE veya özel bağlantı noktası tedarikçisi, belirli bir program için kullanılmak üzere belirli bir DE oluşturmayı desteklemek için [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) uygulayan aynı nesne üzerinde bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [](/cpp/atl/queryinterface) `IDebugProgramNode2` Bu arabirimi edinmek Için arabirim üzerinde QueryInterface 'i çağırın.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugProgramEngines2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|Bu programda hata ayıklayabileceğini tüm olası DEs 'leri gösterir.|
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|Bu programda hata ayıklamak için kullanılacak DE seçimini seçer.|

## <a name="remarks"></a>Açıklamalar
 Kullanıcı tarafından bir devre dışı seçildikten sonra, bu seçenek [SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)çağırarak program düğümüne kaydedilir. Seçili motor, [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)tarafından döndürülen altyapıya dönüşür.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)
