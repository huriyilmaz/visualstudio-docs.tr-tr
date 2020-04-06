---
title: IDebugOutputStringEvent2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugOutputStringEvent2
helpviewer_keywords:
- IDebugOutputStringEvent2 interface
ms.assetid: 86596fd1-cecc-4813-8add-dc3d70068f9b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c47a920e99ece3fb0853e4e6a26dba3c8d0c45c2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726025"
---
# <a name="idebugoutputstringevent2"></a>IDebugOutputStringEvent2
Bu arabirim hata ayıklama altyapısı (DE) tarafından bir dize çıktımı için oturum hata ayıklama yöneticisine (SDM) gönderilir.

## <a name="syntax"></a>Sözdizimi

```
IDebugOutputStringEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE, IDE'nin **Çıkış** penceresine bir dize göndermek için bu arabirimi uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi bu arabirimle aynı nesne üzerinde uygulanmalıdır. SDM `IDebugEvent2` [arabirime](/cpp/atl/queryinterface) erişmek için QueryInterface kullanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE oluşturur ve **Çıkış** penceresine bir dize göndermek için bu olay nesnesi gönderir. Olay, debugged olan programa iliştirildiğinde SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) geri arama işlevi kullanılarak gönderilir.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugOutputStringEvent2`. yöntemini gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetString](../../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)|Görüntülenebilir iletiyi alır.|

## <a name="remarks"></a>Açıklamalar
 Örneğin, yönetilmeyen kodda, çıkarılacak dize, debugged olan program Win32 `OutputDebugString` işlevine bir dize gönderdiğinde kaynaklanabilir. Bu dize DE tarafından ele geçirilir ve `IDebugOutputStringEvent2` olay olarak SDM'ye gönderilir.

 Kullanıcı yanıtı gerektiren bir ileti göndermek için [IDebugMessageEvent2'yi](../../../extensibility/debugger/reference/idebugmessageevent2.md) kullanın.

 Yanıt gerektirmeyen bir hata iletisi göndermek için [IDebugErrorEvent2'yi](../../../extensibility/debugger/reference/idebugerrorevent2.md) kullanın.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
