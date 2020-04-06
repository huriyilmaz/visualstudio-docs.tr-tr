---
title: IDebugField | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c7a25246f42d288020481330fe60e312849862d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728759"
---
# <a name="idebugfield"></a>IDebugField
Bu arabirim, bir alanı, yani bir sembolün veya türün açıklamasını temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugField : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bir sembol sağlayıcı tüm alanlar için taban sınıf olarak bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim tüm alanlar için taban sınıftır. [GetKind'in](../../../extensibility/debugger/reference/idebugfield-getkind.md)iade değerine bağlı olarak, bu arabirim [QueryInterface'i](/cpp/atl/queryinterface)kullanarak daha özel arabirimler döndürebilir. Buna ek olarak, `IDebugField` birçok arabirim nesneleri çeşitli yöntemlerden döndürer.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugField`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Sembol veya tür hakkında görüntülenebilir bilgiler alır.|
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Bir tür alan alır.|
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Alan türünü alır.|
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Alanın konteynerini alır.|
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Alanın adresini alır.|
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Baytlar halinde bir alan büyüklüğünde olur.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Bir alan hakkında genişletilmiş bilgi alır.|
|[Equal](../../../extensibility/debugger/reference/idebugfield-equal.md)|İki alanı karşılaştırır.|
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Sembol veya tür hakkında türbağımsız bilgi alır.|

## <a name="remarks"></a>Açıklamalar
 Bir tür C diline `typedef`eşdeğerdir.

 Aşağıdaki C++ dil örneğinde, `weather` bir sınıf `sunny` `stormy` türü ve semboller vardır:

```cpp
class weather;
weather sunny;
weather stormy;
```

 Bir alanın bir sembolü veya türü temsil edip etmediği [GetKind'i](../../../extensibility/debugger/reference/idebugfield-getkind.md) arayarak ve [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) sonucu inceleyerek belirlenebilir. Bit `FIELD_KIND_TYPE` ayarlanırsa, alan bir türdür ve `FIELD_KIND_SYMBOL` bit ayarlanırsa, bu bir semboldür.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: sh.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
