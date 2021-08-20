---
description: Bu arabirim, kaynak belgedeki bir işlevin soyut konumunu temsil eder.
title: IDebugFunctionPosition2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionPosition2
helpviewer_keywords:
- IDebugFunctionPosition2 interface
ms.assetid: a835f65b-91b0-48ad-8485-04534c814b1b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: ab8fd2348ce7c8e84e38d8b8029c23712620816b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122064168"
---
# <a name="idebugfunctionposition2"></a>IDebugFunctionPosition2
Bu arabirim, kaynak belgedeki bir işlevin soyut konumunu temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugFunctionPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Hata ayıklama altyapısı (DE), bir kaynak belge içindeki bir işlevin konumunu göstermek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim, bekleyen bir kesme noktası oluşturma bölümünde kullanılan [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) yapısının parçası olan bir [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) birleşimin (özellikle de bir [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) yapısı) bir parçası olarak sağlanır.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugFunctionPosition2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetFunctionName](../../../extensibility/debugger/reference/idebugfunctionposition2-getfunctionname.md)|Bu konumun göreli olduğu işlevin adını alır.|
|[GetOffset](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)|İşlevin başından itibaren sapmayı alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim tarafından temsil edilen konum metin tabanlıdır, özellikle de bir [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) yapısıdır.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
