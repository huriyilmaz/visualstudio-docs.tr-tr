---
description: Bu arabirim özel bir özniteliği temsil eder ve özniteliğin adını, üst ve sınıf türünü sağlayabilir.
title: IDebugCustomAttribute | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute
helpviewer_keywords:
- IDebugCustomAttribute interface
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 1007e82474093a04321bb3e550913fdc587f1dacf5d39c75ce9491c095588fb7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121402941"
---
# <a name="idebugcustomattribute"></a>IDebugCustomAttribute
Bu arabirim özel bir özniteliği temsil eder ve özniteliğin adını, üst ve sınıf türünü sağlayabilir.

## <a name="syntax"></a>Syntax

```
IDebugCustomAttribute : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Sembol sağlayıcısı, bir sembol ile ilişkili özel öznitelikleri desteklemek için bu arabirimi uygular. Genellikle kendi nesnesine uygulanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bir [sonraki](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) çağrısı bu arabirimi döndürür. [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) yöntemine yapılan bir çağrı [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) arabirimini döndürür.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugCustomAttribute` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetParentField](../../../extensibility/debugger/reference/idebugcustomattribute-getparentfield.md)|Geçerli özniteliğin eklendiği alanı alır.|
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|Özel öznitelik sınıfı türünü alır.|
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|Özel özniteliğin adını alır.|
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|Öznitelik bilgilerini bayt blobu olarak alır.|

## <a name="remarks"></a>Açıklamalar
 Özel öznitelik, belirli bir sınıf veya yöntemle ilişkili özel meta verileri sağlayan bir C# yapısıdır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: SH. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
