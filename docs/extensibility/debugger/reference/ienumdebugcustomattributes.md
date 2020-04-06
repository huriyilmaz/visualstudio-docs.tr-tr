---
title: IEnumDebugCustomAttributes | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes
helpviewer_keywords:
- IEnumDebugCustomAttributes interface
ms.assetid: 11aa768d-1852-44d6-9de3-17f9bafaded2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f8b521432124267d3f0e179d3a889fb599fa99d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717134"
---
# <a name="ienumdebugcustomattributes"></a>IEnumDebugCustomAttributes
Özel öznitelikleri oyalar.

## <a name="syntax"></a>Sözdizimi

```
IEnumCustomAttributes : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bir sembol sağlayıcısı özel öznitelikleri [(IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) arabirimi aracılığıyla) desteklemek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
- [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) bu arabirimi döndürür.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IEnumDebugCustomAttributes`.

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)|Numaralandırma sırasında belirli sayıda özel öznitelik alır.|
|[Atlamak](../../../extensibility/debugger/reference/ienumdebugcustomattributes-skip.md)|Numaralandırma dizisinde belirli sayıda özel öznitelikleri atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugcustomattributes-reset.md)|Numaralandırma sırasını başa sıfırlar.|
|[Kopyalama](../../../extensibility/debugger/reference/ienumdebugcustomattributes-clone.md)|Geçerli numaralandırma durumuyla aynı numaralandırma durumunu içeren bir numaralandırma oluşturucu oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcustomattributes-getcount.md)|Bir numaralandırmada özel özniteliklerin sayısını alır.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: sh.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
