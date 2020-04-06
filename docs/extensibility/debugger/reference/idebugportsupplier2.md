---
title: IDebugPortSupplier2 | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724478"
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
Bu arabirim, oturum hata ayıklama yöneticisine (SDM) bağlantı noktaları sağlar.

## <a name="syntax"></a>Sözdizimi

```
IDebugPortSupplier2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
Özel bir bağlantı noktası tedarikçisi, bir bağlantı noktası tedarikçisini temsil etmek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
Bağlantı noktası `CoCreateInstance` tedarikçisinin bu `GUID` arabirimi döndürür (bu arabirimi elde etmenin tipik bir yoludur) için yapılan bir arama. Örnek:

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

[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) için yapılan bir çağrı, geçerli bağlantı noktası [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]tedarikçisi tarafından kullanılan temsil eden bu arabirimi döndürür.

- [GetPortSupplier,](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) bağlantı noktasını oluşturan bağlantı noktası tedarikçisini temsil eden bu arabirimi döndürür.

- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) `IDebugPortSupplier` arabirimlerin bir listesini `IEnumDebugPortSuppliers` temsil eder (arayüz [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)elde edilir , [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]kayıtlı tüm liman tedarikçileri temsil eden).

Hata ayıklama altyapısı genellikle bir bağlantı noktası tedarikçisi ile etkileşime girmez.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
Aşağıdaki tabloda `IDebugPortSupplier2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|Liman tedarikçisi adını alır.|
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|Bağlantı noktası tedarikçisi tanımlayıcısını alır.|
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|Liman tedarikçisinden bağlantı noktası alır.|
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|Zaten var olan bağlantı noktalarını oyalar.|
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|Bağlantı noktası tedarikçisinin yeni bağlantı noktaları eklemeyi desteklediğini doğrular.|
|[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|Bir bağlantı noktası ekler.|
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|Bir bağlantı noktasını kaldırır.|

## <a name="remarks"></a>Açıklamalar
Bir liman tedarikçisi kendisini ad ve kimlikle tanımlayabilir, bağlantı noktaları ekleyebilir ve kaldırabilir ve bağlantı noktası tedarikçisinin sağladığı tüm bağlantı noktalarını sayabilir.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
