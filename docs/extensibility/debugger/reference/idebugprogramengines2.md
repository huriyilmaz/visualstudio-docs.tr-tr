---
title: IDebugProgramEngines2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2
helpviewer_keywords:
- IDebugProgramEngines2 interface
ms.assetid: 53d648f0-6c11-4337-badd-c43f3872b62c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94df9acc6a0478ba2cb36022bc8618c69be97b8c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722392"
---
# <a name="idebugprogramengines2"></a>IDebugProgramEngines2
Bu arabirim, program düğümleri tarafından, bu programı hata ayıklama olabilecek tüm olası hata ayıklama altyapılarını (DE) belirtmek için kullanılır.

## <a name="syntax"></a>Sözdizimi

```
IDebugProgramEngines2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bir DE veya özel bağlantı noktası tedarikçisi belirli bir program için kullanılmak üzere belirli bir DE kurulmasını desteklemek için [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) uygulayan aynı nesne üzerinde bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi `IDebugProgramNode2` elde etmek için [queryinterface'i](/cpp/atl/queryinterface) bir arabirimden arayın.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugProgramEngines2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|Bu program hata ayıklamak olabilir tüm olası DEs gösterir.|
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|Bu programın hata ayıklama için kullanılacak DE'sini seçer.|

## <a name="remarks"></a>Açıklamalar
 Kullanıcı tarafından bir DE seçildikten sonra, bu seçim [SetEngine'i](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)arayarak program düğümüne kaydedilir. Seçilen motor [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)tarafından döndürülen motor olur.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)
