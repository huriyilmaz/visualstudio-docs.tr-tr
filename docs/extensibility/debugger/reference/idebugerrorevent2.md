---
title: IDebugErrorEvent2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorEvent2
helpviewer_keywords:
- IDebugErrorEvent2 interface
ms.assetid: 275b6f38-b3d4-4cae-8491-491177f524fb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 00fd8b4b42f11d18958f8a969bc4ccd58754ab93
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730006"
---
# <a name="idebugerrorevent2"></a>IDebugErrorEvent2
Bu arabirim, kullanıcıya bildirilecek bir hata iletisi belirtir.

## <a name="syntax"></a>Sözdizimi

```
IDebugErrorEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE) hataları insan tarafından okunabilir iletiler olarak bildirmek için bu arabirimi uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi bu arabirimle aynı nesne üzerinde uygulanmalıdır. SDM `IDebugEvent2` [arabirime](/cpp/atl/queryinterface) erişmek için QueryInterface kullanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE oluşturur ve bir hata bildirmek için bu olay nesnesi gönderir. Olay, sdm tarafından verilen [iDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) geri arama işlevi kullanılarak gönderilir.

## <a name="methods-in-vtable-order"></a>Vtable sırasına göre yöntemler
 Bu arabirim aşağıdaki yöntemi uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|`GetErrorMessage`|İnsan tarafından okunabilir bir dize olarak bir hata döndürür.|

## <a name="remarks"></a>Açıklamalar
 Hata ayıklama altyapısı bir hatayla karşılaşırsa, visual studio aracılığıyla iletiyi kullanıcıya bildirmek için bu arabirimi kullanabilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
