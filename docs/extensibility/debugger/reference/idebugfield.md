---
description: Bu arabirim bir alanı, yani bir simgenin veya türün açıklamasını temsil eder.
title: IDebugField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: c38865ba18dfbc0020379a33c5becdb7440e406d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122088763"
---
# <a name="idebugfield"></a>IDebugField
Bu arabirim bir alanı, yani bir simgenin veya türün açıklamasını temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugField : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Sembol sağlayıcısı bu arabirimi tüm alanlar için temel sınıf olarak kullanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim tüm alanlar için temel sınıftır. [GetKind'in](../../../extensibility/debugger/reference/idebugfield-getkind.md)dönüş değerine bağlı olarak, bu arabirim QueryInterface kullanarak daha özel [arabirimler getirebilirsiniz.](/cpp/atl/queryinterface) Buna ek olarak, birçok arabirim `IDebugField` çeşitli yöntemlerden nesneleri geri döner.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugField` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Sembol veya tür hakkında değiştirilebilir bilgileri alır.|
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Alan türlerini alır.|
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Alan türünü alır.|
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Alanın kapsayıcısı alır.|
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Alanın adresini alır.|
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Bir alanın boyutunu bayt cinsinden alır.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Bir alan hakkında genişletilmiş bilgileri alır.|
|[Eşit](../../../extensibility/debugger/reference/idebugfield-equal.md)|İki alanı karşılar.|
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Sembol veya tür hakkında türden bağımsız bilgileri alır.|

## <a name="remarks"></a>Açıklamalar
 Tür, C diline `typedef` eşdeğerdir.

 Aşağıdaki C++ dili örneğinde, `weather` bir sınıf türü ve `sunny` `stormy` simgelerdir:

```cpp
class weather;
weather sunny;
weather stormy;
```

 Bir alanın bir simgeyi veya türü temsil edip [ettiği, GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) çağrılarak ve sonucun FIELD_KIND [belirlenebilirsiniz.](../../../extensibility/debugger/reference/field-kind.md) Bit `FIELD_KIND_TYPE` ayarlanırsa alan bir türdür ve `FIELD_KIND_SYMBOL` bit ayarlanmışsa bir semboldür.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: sh.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
