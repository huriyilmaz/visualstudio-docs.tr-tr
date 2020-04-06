---
title: IDebugPortSupplier3 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f015c21f71f064f2302660ebc75ef00a245348c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724442"
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
Bu arabirim, bir arayanın bağlantı noktası tedarikçisinin hata ayıklama çağrıları arasında bağlantı noktalarını koruyup koruyamayacağını (diske yazarak) ve ardından korunan bağlantı noktalarının listesini alıp alamadığını belirlemesine olanak tanır.

## <a name="syntax"></a>Sözdizimi

```
IDebugPortSupplier3 : IDebugPortSupplier2
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Özel bir bağlantı noktası tedarikçisi, bağlantı noktası bilgilerinin kalıcı olmasını veya diske kaydedilmesi için bu arabirimi uygular. Bu [arabirim, IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) arabirimi yle aynı nesne üzerinde uygulanmalıdır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi `IDebugPortSupplier2` elde etmek için arabirimdeki [QueryInterface'i](/cpp/atl/queryinterface) arayın.

## <a name="methods-in-vtable-order"></a>Vtable sırasına göre yöntemler
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) arabiriminden devralınan yöntemlere ek olarak, bu arabirim aşağıdakileri destekler:

|Yöntem|Açıklama|
|------------|-----------------|
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Bağlantı noktası tedarikçisinin hata ayıklama çağrıları arasında bağlantı noktalarını (diske yazarak) devam edip edemeyeceğini verir.|
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Bu bağlantı noktası tedarikçisi tarafından diske yazılmış tüm bağlantı noktalarını bulmak için kullanılabilecek bir nesne döndürür.|

## <a name="remarks"></a>Açıklamalar
 Bir bağlantı noktası tedarikçisi, çağrılması arasında bağlantı noktalarını devam ettirebiliyorsa, bu arabirimi uygulamalıdır. Bağlantı noktası tedarikçisi anında yüklendiğinde bağlantı noktaları yüklenmeli ve bağlantı noktası tedarikçisi yok edildiğinde diske yazılmalıdır.

 Hata ayıklama altyapısı genellikle bir bağlantı noktası tedarikçisi ile etkileşime girmez ve bu arabirim için hiçbir kullanımı olmayacaktır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
