---
description: Bu arabirim, bir bağlantı noktasının sunucusuna ve bildirim özelliklerine erişmek için çeşitli yöntemler sağlar.
title: IDebugDefaultPort2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: a606358b708b49f866063eeefc25b4e0c3fec44cab9fa8689492a475faeb3749
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121417502"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
Bu arabirim, bir bağlantı noktasının sunucusuna ve bildirim özelliklerine erişmek için çeşitli yöntemler sağlar.

## <a name="syntax"></a>Syntax

```
IDebugDefaultPort2 : IDebugPort2
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Visual Studio, programlara erişmek için hata ayıklama bağlantı noktasını temsil etmek için bu arabirimi uygulamaya almaktadır. Özel bir bağlantı noktası sağlayıcı, uzaktan hata ayıklamayı gerçekleştirebilirse bu arabirimi de kullanabilir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [IDebugProgramProvider2 arabiriminde yöntemlerin](../../../extensibility/debugger/reference/idebugprogramprovider2.md) bağımsız değişkeni bu arabirimi sağlar. [IDebugPort2 arabiriminde](../../../extensibility/debugger/reference/idebugport2.md) [QueryInterface](/cpp/atl/queryinterface) çağrısı da bu arabirimi elde edebilirsiniz.

## <a name="methods-in-vtable-order"></a>Vtable sırasına göre yöntemler
 [Bu arabirim, IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)içinde tanımlanan yöntemlere ek olarak aşağıdaki yöntemleri de kullanır:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Bu bağlantı noktası bağlantı noktası bildirim arabirimini alır.|
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Bu bağlantı noktasını barındıran sunucunun arabirimini alır.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Bu bağlantı noktasının yerel makinede çalıştırıp çalışmay olmadığını belirler.|

## <a name="remarks"></a>Açıklamalar
 " " adı, varsayılan bir bağlantı noktasını temsil etmeyer şekilde yanlış `IDebugDefaultPort2` bir addır. "IDebugPort3" olarak da adlandırılan bir dosyadır.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
