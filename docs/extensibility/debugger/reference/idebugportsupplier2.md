---
title: IDebugPortSupplier2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2
helpviewer_keywords:
- IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ddce454e6634d8cc177019e9d30b0ffcc7e7f1cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80724478"
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
Bu arabirim, oturum hata ayıklama Yöneticisi 'ne (SDM) bağlantı noktaları sağlar.

## <a name="syntax"></a>Syntax

```
IDebugPortSupplier2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
Özel bir bağlantı noktası sağlayıcısı, bir bağlantı noktası tedarikçiyi göstermek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
`CoCreateInstance`Bir bağlantı noktası tedarikçisine yapılan bir çağrı `GUID` Bu arabirimi döndürür (Bu, bu arabirimi elde etmenin tipik yoludur). Örneğin:

```cpp
IDebugPortSupplier2 *GetPortSupplier(GUID *pPortSupplierGuid)
{
    IDebugPortSupplier2 *pPS = NULL;
    if (pPortSupplierGuid != NULL) {
        CComPtr<IDebugPortSupplier2> spPortSupplier;
        spPortSupplier.CoCreateInstance(*pPortSupplierGuid);
        if (spPortSupplier != NULL) {
            pPS = spPortSupplier.Detach();
        }
    }
    return (pPS);
}
```

[Getporttedarikçinin](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) çağrısı, tarafından kullanılan geçerli bağlantı noktası tedarikçiyi temsil eden bu arabirimi döndürür [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] .

- [Getporttedarikçinin](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) , bağlantı noktasını oluşturan bağlantı noktası tedarikçiyi temsil eden bu arabirimi döndürür.

- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) bir arabirim listesini temsil eder `IDebugPortSupplier` ( `IEnumDebugPortSuppliers` arabirim, [tralınttedarikçilerinizden](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)elde edilir ve ile kayıtlı olan tüm bağlantı noktası tedarikçilerini temsil eder [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ).

Bir hata ayıklama altyapısı genellikle bir bağlantı noktası sağlayıcısıyla etkileşime girmez.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugPortSupplier2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|Bağlantı noktası tedarikçinin adını alır.|
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|Bağlantı noktası sağlayıcısı tanımlayıcısını alır.|
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|Bir bağlantı noktası tedarikçiden bir bağlantı noktası alır.|
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|Zaten var olan bağlantı noktalarını numaralandırır.|
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|Bir bağlantı noktası üreticisinin yeni bağlantı noktası eklemeyi desteklediğini doğrular.|
|[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|Bir bağlantı noktası ekler.|
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|Bir bağlantı noktasını kaldırır.|

## <a name="remarks"></a>Açıklamalar
Bir bağlantı noktası sağlayıcısı kendisini ad ve KIMLIĞE göre tanımlayabilir, bağlantı noktaları ekleyebilir ve kaldırabilir ve bağlantı noktası tedarikçinin sağladığı tüm bağlantı noktalarını numaralandırabilirsiniz.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
