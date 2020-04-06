---
title: IEnumDebugAdresleri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses
helpviewer_keywords:
- IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14b42ec37babe72b47b0e832397d33029c4fc3d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717588"
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
Bu [arabirim, IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) arabirimini uygulayan nesnelerin bir koleksiyonunu temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IEnumDebugAdresses : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bu arabirim, [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) arabirimini uygulayan nesne kümeleri sağlamak için sembol sağlayıcı tarafından uygulanır. GetCount yönteminin varlığı nedeniyle bunun standart bir COM [GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md) numaralandırması olmadığını unutmayın.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) ve [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)tarafından döndürülür.

## <a name="methods-in-vtable-order"></a>Vtable sırasına göre yöntemler
 Bu arabirim aşağıdaki yöntemleri uygular.

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|Bir sonraki [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) nesnelerini numaralandırmadan alır.|
|[Atlamak](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|Belirli sayıda girişi atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|Numaralandırmayı ilk girişe sıfırlar.|
|[Kopyalama](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|Geçerli numaralandırmanın bir kopyasını alır.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|Numaralandırmadaki giriş sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim genellikle ifade değerlendiricisivermek için uygun adresi belirlemeye yardımcı olmak için hata ayıklama altyapısı tarafından kullanılır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: sh.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
