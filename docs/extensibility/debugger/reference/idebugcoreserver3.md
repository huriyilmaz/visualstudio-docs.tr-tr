---
description: Bu arabirim, işlemin üzerinde çalıştığı sunucu hakkındaki bilgilere erişim sağlar.
title: IDebugCoreServer3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 38e839ef5c653bfe21541371f8320c74cfa4679b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122127369"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
Bu arabirim, işlemin üzerinde çalıştığı sunucu hakkındaki bilgilere erişim sağlar.

## <a name="syntax"></a>Syntax

```
IDebugCoreServer3 : IDebugCoreServer2
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Visual Studio bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi bir [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) arabiriminden almak için [QueryInterface](/cpp/atl/queryinterface) kullanın. [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) çağrısı da bu arabirimi döndürebilir. Bu arabirim, genellikle bir sunucu üzerinde programları (yerel veya uzak) başlatmak için özel bir bağlantı noktası sağlayıcısı tarafından en sık kullanılır.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) arabirimindeki yöntemlere ek olarak, bu arabirim aşağıdaki yöntemleri uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|Sunucunun adını alır.|
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|Sunucu adının kolay bir sürümünü alır|
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|Belirli hata ayıklama altyapılarının, bu süreçler başlatıldığında otomatik olarak işlemlere eklemesini söyler.|
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|Otomatik iliştirme başarısız olduğunda belirli bir hata kodunu alır.|
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|Sunucuda hata ayıklama altyapısının bir örneğini oluşturur.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|Sunucunun çağıranın aynı makinede olup olmadığını belirten bir bayrak alır.|
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|Sunucusuyla iletişim kurmak için kullanılan protokolü gösteren bir değer alır.|
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|Bu sunucunun bildiği tüm hata ayıklama motorları için otomatik iliştirme ayarlarını devre dışı bırakır.|

## <a name="remarks"></a>Açıklamalar
 Özel bir bağlantı noktası sağlayıcısı, bir [olay](../../../extensibility/debugger/reference/idebugportevents2-event.md)çağrısında [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) arabirimini alır. `IDebugCoreServer3`Arabirim, bu arabirimden elde edilebilir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
