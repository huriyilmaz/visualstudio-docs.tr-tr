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
ms.openlocfilehash: 20fe0885186fefd2514be40e04cb27f3d92220c579f02f5679b48cabefde5c59
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121415409"
---
# <a name="ienumdebugfields"></a>IEnumDebugFields
Bu [arabirim, IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabirimini uygulayan bir nesne koleksiyonunu temsil eder.

## <a name="syntax"></a>Syntax

```
IEnumDebugFields : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bu arabirim, [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabirimini uygulayan nesne kümeleri sağlamak için sembol sağlayıcısı tarafından uygulanır. [GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md) yönteminin var olması nedeniyle bunun standart bir COM numaralama olmadığını unutmayın.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md) ve [GetNamespacesUsedAtAddress tarafından döndürülür.](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)

## <a name="methods-in-vtable-order"></a>Vtable sırasına göre yöntemler
 Bu arabirim aşağıdaki yöntemleri kullanır.

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|Bir sonraki [IDebugField nesnelerini](../../../extensibility/debugger/reference/idebugfield.md) numaralandırmadan alın.|
|[Atla](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|Belirtilen sayıda girdiyi atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|Numaralamayı ilk girişe sıfırlar.|
|[Kopyalama](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|Geçerli numaralamanın bir kopyasını alın.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|Numaralamada girdi sayısını alın.|

## <a name="remarks"></a>Açıklamalar

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: sh.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)
- [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)
