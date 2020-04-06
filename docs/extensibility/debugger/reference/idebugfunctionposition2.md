---
title: IDebugFunctionPosition2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionPosition2
helpviewer_keywords:
- IDebugFunctionPosition2 interface
ms.assetid: a835f65b-91b0-48ad-8485-04534c814b1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c260b6316207b0079a2ca8893b851db8b1288ba6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728316"
---
# <a name="idebugfunctionposition2"></a>IDebugFunctionPosition2
Bu arabirim, kaynak belgedeki bir işlevin soyut konumunu temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugFunctionPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE), bir işlevin kaynak belge içindeki konumunu temsil etmek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim, bekleyen bir kesme noktası oluştururken kullanılan [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) yapının sırayla bir parçası olan [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) birleşimin (özellikle [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) bir yapının) bir parçası olarak sağlanır.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugFunctionPosition2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetFunctionName](../../../extensibility/debugger/reference/idebugfunctionposition2-getfunctionname.md)|Bu konumun göreli olduğu işlevin adını alır.|
|[GetOffset](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)|İşlevin başlangıcından itibaren ofset alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim tarafından temsil edilen konum metin tabanlı, [özellikle, TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) bir yapıdır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
