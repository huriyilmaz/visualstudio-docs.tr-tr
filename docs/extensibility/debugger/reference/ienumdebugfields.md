---
description: Bu arabirim, IDebugField arabirimini uygulayan bir nesne koleksiyonunu temsil eder.
title: IEnumDebugFields | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields
helpviewer_keywords:
- IEnumDebugFields interface
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: bd98cd2d27c7693b5c5fb991125355ff92e60b82
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122125640"
---
# <a name="ienumdebugfields"></a>IEnumDebugFields
Bu arabirim, [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabirimini uygulayan bir nesne koleksiyonunu temsil eder.

## <a name="syntax"></a>Syntax

```
IEnumDebugFields : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bu arabirim, [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabirimini uygulayan nesne kümeleri sağlamak için sembol sağlayıcısı tarafından uygulanır. [GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md) yönteminin varlığı nedeniyle bu standart bir com numaralandırması olmadığını unutmayın.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim [Getmethodalanları byname](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md) ve [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)tarafından döndürülür.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Bu arabirim aşağıdaki yöntemleri uygular.

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|Numaralandırmadaki [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesnelerinin bir sonraki kümesini alır.|
|[Atla](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|Belirtilen sayıda girişi atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|Numaralandırmayı ilk girdiye sıfırlar.|
|[Kopyalama](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|Geçerli numaralandırmanın bir kopyasını alır.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|Numaralandırmadaki giriş sayısını alır.|

## <a name="remarks"></a>Açıklamalar

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: SH. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)
- [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)
