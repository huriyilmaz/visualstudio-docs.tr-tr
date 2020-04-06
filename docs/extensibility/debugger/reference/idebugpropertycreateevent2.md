---
title: IDebugPropertyCreateEvent2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyCreateEvent2
helpviewer_keywords:
- IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84d8fcb4375f29820b51752ac3fdebbd04f06f80
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720922"
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
Bu arabirim, hata ayıklama altyapısı (DE) tarafından, belirli bir belgeyle ilişkili bir özellik oluşturduğunda oturum hata ayıklama yöneticisine (SDM) gönderilir.

## <a name="syntax"></a>Sözdizimi

```
IDebugPropertyCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE, bir özelliğin oluşturulduğunu bildirmek için bu arabirimi uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi bu arabirimle aynı nesne üzerinde uygulanmalıdır. SDM `IDebugEvent2` [arabirime](/cpp/atl/queryinterface) erişmek için QueryInterface kullanır. De yüklenen veya oluşturulmuş bir komut dosyası ile ilişkili bir özellik oluşturdu ve bu komut dosyası IDE görünmesi gerekiyorsa bu arabirim uygulanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE oluşturur ve oluşturulan bir özellik bildirmek için bu olay nesnesi gönderir. Olay, debugged olan programa iliştirildiğinde SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) geri arama işlevi kullanılarak gönderilir.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tablo arabirimin yöntemini `IDebugPropertyCreateEvent2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|Yeni mülkü alır.|

## <a name="remarks"></a>Açıklamalar
 Bir özelliğin bununla ilişkili belirli bir belgesi veya komut dosyası varsa, DE bu olayı Belgenin adı ile **Komut Dosyası Belgeleri** penceresini güncelleştirmek için SDM'ye gönderebilir. SDM, [IUnknown](/cpp/atl/iunknown) işaretçisi `guidDocument` içeren bir `VARIANT` işaretçi almak için bağımsız değişkenle [GetExtendedInfo'yu](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) arayacaktır. SDM, **Komut Dosyası Belgeleri** penceresini güncelleştirmek için kullanılan [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) arabirimini almak için bu işaretçide [QueryInterface'i](/cpp/atl/queryinterface) arayacaktır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
