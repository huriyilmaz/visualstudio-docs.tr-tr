---
description: Bu arabirim, IDebugAddress arabirimini uygulayan bir nesne koleksiyonunu temsil eder.
title: IEnumDebugAddresses | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses
helpviewer_keywords:
- IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ea9e4115c1664e1dcd05041f7ece056b5de01dae
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222646"
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
Bu arabirim, [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) arabirimini uygulayan bir nesne koleksiyonunu temsil eder.

## <a name="syntax"></a>Syntax

```
IEnumDebugAdresses : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bu arabirim, [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) arabirimini uygulayan nesne kümeleri sağlamak için sembol sağlayıcısı tarafından uygulanır. [GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md) yönteminin varlığı nedeniyle bu standart bir com numaralandırması olmadığını unutmayın.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) ve [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)tarafından döndürülür.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Bu arabirim aşağıdaki yöntemleri uygular.

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|Numaralandırmadaki [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) nesnelerinin bir sonraki kümesini alır.|
|[Atla](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|Belirtilen sayıda girişi atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|Numaralandırmayı ilk girdiye sıfırlar.|
|[Oluşturulacak](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|Geçerli numaralandırmanın bir kopyasını alır.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|Numaralandırmadaki giriş sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim genellikle hata ayıklama altyapısı tarafından, ifade değerlendiricisi 'ne verilecek uygun adresi belirlemede yardımcı olması için kullanılır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: SH. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
