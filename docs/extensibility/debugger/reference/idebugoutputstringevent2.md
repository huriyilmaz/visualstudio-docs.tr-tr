---
title: IDebugOutputStringEvent2 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726025"
---
# <a name="idebugoutputstringevent2"></a>IDebugOutputStringEvent2
Bu arabirim, hata ayıklama altyapısı (DE) tarafından bir dizeyi çıkarmak için oturum hata ayıklama Yöneticisi 'ne (SDM) gönderilir.

## <a name="syntax"></a>Syntax

```
IDebugOutputStringEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bu, IDE 'nin **Çıkış** penceresine bir dize göndermek için de bu arayüzü uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabiriminin bu arabirimle aynı nesne üzerinde uygulanması gerekir. SDM, arabirime erişmek için [QueryInterface](/cpp/atl/queryinterface) kullanır `IDebugEvent2` .

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE, **çıktı** penceresine bir dize göndermek için bu olay nesnesini oluşturur ve gönderir. Olay, ayıklanmakta olan programa eklendiği zaman SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) callback işlevi kullanılarak gönderilir.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemi gösterilmektedir `IDebugOutputStringEvent2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetString](../../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)|Görüntülenebilen iletiyi alır.|

## <a name="remarks"></a>Açıklamalar
 Örneğin, yönetilmeyen kodda, hata ayıklanan programın Win32 işlevine bir dize göndermesi durumunda çıkış olacak dize bu olabilir `OutputDebugString` . Bu dize, DE tarafından yakalanarak olay olarak SDM 'ye gönderilir `IDebugOutputStringEvent2` .

 Kullanıcı yanıtı gerektiren bir ileti göndermek için [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) kullanın.

 Yanıt gerektirmeyen bir hata iletisi göndermek için [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) kullanın.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
