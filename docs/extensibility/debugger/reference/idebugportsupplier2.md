---
description: Bu arabirim oturum hata ayıklama yöneticisine (SDM) bağlantı noktaları sağlar.
title: IDebugPortSupplier2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2
helpviewer_keywords:
- IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: ded700cb5f9e6c7ff725f0b7049842d3e308b014
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122088113"
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
Bu arabirim oturum hata ayıklama yöneticisine (SDM) bağlantı noktaları sağlar.

## <a name="syntax"></a>Syntax

```
IDebugPortSupplier2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
Özel bir bağlantı noktası sağlayıcı, bu arabirimi bir bağlantı noktası sağlayıcıyı temsil edecek şekilde uygulamaya almaktadır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
Bir bağlantı `CoCreateInstance` noktası sağlayıcının çağrısı bu `GUID` arabirimi döndürür (bu arabirimi elde etmek için tipik bir yol). Örnek:

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

[GetPortSupplier çağrısı,](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) tarafından kullanılan geçerli bağlantı noktası sağlayıcıyı temsil eden bu arabirimi [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] döndürür.

- [GetPortSupplier,](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) bağlantı noktasını oluşturan bağlantı noktası sağlayıcıyı temsil eden bu arabirimi döndürür.

- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) bir arabirim listesini temsil eder `IDebugPortSupplier` (arabirim `IEnumDebugPortSuppliers` [EnumPortSuppliers'dan](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)alınarak ile kaydedilen tüm bağlantı noktası sağlayıcılarını temsil [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] eder).

Hata ayıklama altyapısı genellikle bir bağlantı noktası tedarikçiyle etkileşim kurmaz.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
Aşağıdaki tabloda yöntemlerini `IDebugPortSupplier2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|Bağlantı noktası sağlayıcı adını alır.|
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|Bağlantı noktası sağlayıcı tanımlayıcısını alır.|
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|Bir bağlantı noktası sağlayıcıdan bağlantı noktası alır.|
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|Zaten var olan bağlantı noktalarını numaralar.|
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|Bir bağlantı noktası sağlayıcının yeni bağlantı noktaları eklemeyi desteklediğini doğrular.|
|[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|Bir bağlantı noktası ekler.|
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|Bir bağlantı noktasını kaldırır.|

## <a name="remarks"></a>Açıklamalar
Bir bağlantı noktası sağlayıcı kendisini adına ve kimliğine göre tanımlayabilir, bağlantı noktalarını ekp kaldırabilir ve bağlantı noktası sağlayıcının sağladığı tüm bağlantı noktalarını numaralara ekleyebilir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
