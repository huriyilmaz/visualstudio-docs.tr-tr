---
title: IEnumDebugObjects | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects
helpviewer_keywords:
- IEnumDebugObjects interface
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c04409fb695613fea5d54b285946c04719fbe5b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80716255"
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için lütfen bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Bu arabirim, [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) arabirimini uygulayan bir nesne koleksiyonunu temsil eder.

## <a name="syntax"></a>Syntax

```
IEnumDebugObjects : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 İfade değerlendirici, [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) arabirimini uygulayan nesne kümeleri sağlamak için bu arabirimi uygular. [GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md) yönteminin varlığı nedeniyle bu standart bir com numaralandırması olmadığını unutmayın.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md) bu arabirimi döndürür.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Bu arabirim aşağıdaki yöntemleri uygular.

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|Numaralandırmadaki [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesnelerinin bir sonraki kümesini alır.|
|[Atla](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|Belirtilen sayıda girişi atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|Numaralandırmayı ilk girdiye sıfırlar.|
|[Kopyalama](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|Geçerli numaralandırmanın bir kopyasını alır.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|Numaralandırmadaki giriş sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim bir hata ayıklama altyapısının bir dizideki nesne kümesi üzerinde listeleme yapmasına izin verir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: ee. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)
