---
description: Bu arabirim, bir dize çıkışı için hata ayıklama altyapısı (DE) tarafından oturum hata ayıklama yöneticisine (SDM) gönderilir.
title: IDebugOutputStringEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugOutputStringEvent2
helpviewer_keywords:
- IDebugOutputStringEvent2 interface
ms.assetid: 86596fd1-cecc-4813-8add-dc3d70068f9b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 6480b1018726d37d4bd51af5d3c4d66b8b42a9a56f04aceb530518876bd078a4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121307147"
---
# <a name="idebugoutputstringevent2"></a>IDebugOutputStringEvent2
Bu arabirim, bir dize çıkışı için hata ayıklama altyapısı (DE) tarafından oturum hata ayıklama yöneticisine (SDM) gönderilir.

## <a name="syntax"></a>Syntax

```
IDebugOutputStringEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE, IDE'nin Çıkış penceresine bir dize **göndermek** için bu arabirimi uygulamaya alır. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi, bu arabirimle aynı nesne üzerinde uygulanarak uygulanarak. SDM, [arabirime erişmek için QueryInterface](/cpp/atl/queryinterface) `IDebugEvent2` kullanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE bu olay nesnesini oluşturur ve çıkış penceresine bir dize **göndermek için** gönderir. Olay, hata ayıklama yapılan programa ekli olduğunda SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) geri çağırma işlevi kullanılarak gönderilir.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemini `IDebugOutputStringEvent2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetString](../../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)|Görüntülenebilir iletiyi alır.|

## <a name="remarks"></a>Açıklamalar
 Örneğin, beklenemeyen kodda, hata ayıklandığı program Win32 işlevine bir dize gönderdiğinde çıkış olarak dizenin kaynağı `OutputDebugString` olabilir. Bu dize DE tarafından kesme noktası alır ve olay olarak SDM'ye `IDebugOutputStringEvent2` gönderilir.

 Kullanıcı [yanıtı gerektiren bir ileti göndermek için IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) kullanın.

 Yanıt gerektirmeyen bir hata iletisi göndermek için [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) kullanın.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
