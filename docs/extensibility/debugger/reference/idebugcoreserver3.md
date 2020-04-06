---
title: IDebugCoreServer3 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d110e66e937249fdee34f424d4f68a9b914113d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732814"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
Bu arabirim, işlemin yürüttürünsunucuyla ilgili bilgilere erişim sağlar.

## <a name="syntax"></a>Sözdizimi

```
IDebugCoreServer3 : IDebugCoreServer2
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Visual Studio bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi [bir IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) arabiriminden elde etmek için [QueryInterface'i](/cpp/atl/queryinterface) kullanın. [GetServer'a](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) yapılan bir arama da bu arabirimi döndürebilir. Bu arabirim, programları sunucuda (yerel veya uzak) başlatmak için özel bir bağlantı noktası tedarikçisi tarafından en sık kullanılır.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) arabirimindeki yöntemlere ek olarak, bu arabirim aşağıdaki yöntemleri uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|Sunucunun adını alır.|
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|Sunucu adının kolay bir sürümünü alır|
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|Belirli hata ayıklama motorlarına, bu işlemler başladığında işlemlere otomatik olarak bağlanmasını söyler.|
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|Otomatik ekleme başarısız olduğunda belirli bir hata kodu alır.|
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|Sunucuda hata ayıklama altyapısı örneği oluşturur.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|Sunucunun arayanla aynı makinede olup olmadığını belirten bir bayrak alır.|
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|Sunucuyla iletişim kurmak için kullanılan protokolü gösteren bir değer alır.|
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|Sunucunun bildiği tüm hata ayıklama motorları için tüm otomatik ekleme ayarlarını devre dışı kılmaktadır.|

## <a name="remarks"></a>Açıklamalar
 Özel bir bağlantı noktası tedarikçisi [Olay](../../../extensibility/debugger/reference/idebugportevents2-event.md)bir çağrı [iDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) arabirimi alır. Arayüz `IDebugCoreServer3` bu arabirimden elde edilebilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
