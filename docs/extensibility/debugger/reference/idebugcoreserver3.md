---
description: Bu arabirim, işlemi çalıştıran sunucu hakkında bilgilere erişim sağlar.
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
ms.openlocfilehash: 7ab3323f7377f31e187dbb2642781ca54584b762d8c616ea9cba3eb37f50c3c5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121377796"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
Bu arabirim, işlemi çalıştıran sunucu hakkında bilgilere erişim sağlar.

## <a name="syntax"></a>Syntax

```
IDebugCoreServer3 : IDebugCoreServer2
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Visual Studio arabirimini uygulayan bir uygulamadır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi [bir IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) arabiriminden almak için [QueryInterface](/cpp/atl/queryinterface) kullanın. [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) çağrısı bu arabirimi de geri getirebilirsiniz. Bu arabirim genellikle özel bağlantı noktası sağlayıcıları tarafından programları bir sunucuda (yerel veya uzak) başlatmak için kullanılır.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 [Bu arabirim, IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) arabiriminde yöntemlere ek olarak aşağıdaki yöntemleri de kullanır:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|Sunucunun adını verir.|
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|Sunucu adının kolay bir sürümünü alma|
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|Belirli hata ayıklama altyapılarının, bu işlemler başlatılırken işlemlere otomatik olarak iliştirmelerini söyler.|
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|Otomatik ekleme başarısız olduğunda belirli bir hata kodunu alır.|
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|Sunucuda bir hata ayıklama altyapısı örneği oluşturur.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|Sunucunun çağıranla aynı makinede olup olmadığını belirten bir bayrak verir.|
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|Sunucuyla iletişim kurmak için kullanılan protokolü belirten bir değer verir.|
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|Bu sunucunun bildiği tüm hata ayıklama altyapıları için tüm otomatik ekleme ayarlarını devre dışı verir.|

## <a name="remarks"></a>Açıklamalar
 Özel bir bağlantı noktası sağlayıcı, [Event çağrısında IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) arabirimini [alır.](../../../extensibility/debugger/reference/idebugportevents2-event.md) Arabirim `IDebugCoreServer3` bu arabirimden edinebilirsiniz.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
