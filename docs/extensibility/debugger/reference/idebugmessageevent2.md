---
description: bu arabirim, hata ayıklama altyapısı (DE) tarafından kullanıcıdan yanıt gerektiren Visual Studio bir ileti göndermek için kullanılır.
title: IDebugMessageEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 4940d8d19c76b9e64da4dbbb3b659519bace24e3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122126992"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
bu arabirim, hata ayıklama altyapısı (DE) tarafından kullanıcıdan yanıt gerektiren Visual Studio bir ileti göndermek için kullanılır.

## <a name="syntax"></a>Syntax

```
IDebugMessageEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 bu arabirimi, bir kullanıcı yanıtı gerektiren Visual Studio ileti göndermek için DE uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabiriminin bu arabirimle aynı nesne üzerinde uygulanması gerekir. SDM, arabirime erişmek için [QueryInterface](/cpp/atl/queryinterface) kullanır `IDebugEvent2` .

 bu arabirimin uygulanması, ' nin DE [setresponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) çağrısını Visual Studio iletmelidir. Örneğin, bu, bunun ileti işleme iş parçacığına postalanan bir ileti ile yapılabilir veya bu arabirimi uygulayan nesne DE DE bir başvuru tutabilir ve buna geçilen Yanıt ile geri çağrı yapabilir `IDebugMessageEvent2::SetResponse` .

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE, bir yanıt gerektiren kullanıcıya bir ileti göstermek için bu olay nesnesini oluşturur ve gönderir. Olay, ayıklanmakta olan programa eklendiği zaman SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) callback işlevi kullanılarak gönderilir.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugMessageEvent2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Görüntülenecek iletiyi alır.|
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|İleti kutusundan yanıtı (varsa) ayarlar.|

## <a name="remarks"></a>Açıklamalar
 Ayrıca, kullanıcıdan belirli bir ileti için belirli bir yanıt gerekiyorsa bu arabirimi kullanır. örneğin, bir programa uzaktan iliştirme denemesinden sonra da "erişim reddedildi" iletisi alırsa, bu özel iletiyi `IDebugMessageEvent2` ileti kutusu stiliyle bir olayda Visual Studio gönderir `MB_RETRYCANCEL` . Bu, kullanıcının iliştirme işlemini yeniden denemesini veya iptal etmesine olanak tanır.

 Ayrıca, bu iletinin Win32 işlevinin kurallarını izleyerek nasıl işleneceğini belirtir `MessageBox` (Ayrıntılar için bkz. [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) ).

 kullanıcıdan yanıt gerektirmeyen Visual Studio ileti göndermek için [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) arabirimini kullanın.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
