---
title: IDebugMessageEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6796e2d4f3a7fa20e4bcab4088b6687866edf570
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928269"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
Bu arabirim, hata ayıklama altyapısı (DE) tarafından kullanıcıdan yanıt gerektiren bir Visual Studio 'ya ileti göndermek için kullanılır.

## <a name="syntax"></a>Syntax

```
IDebugMessageEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bu arabirimi, bir kullanıcı yanıtı gerektiren Visual Studio 'ya bir ileti göndermek için DE uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabiriminin bu arabirimle aynı nesne üzerinde uygulanması gerekir. SDM, arabirime erişmek için [QueryInterface](/cpp/atl/queryinterface) kullanır `IDebugEvent2` .

 Bu arabirimin uygulanması, Visual Studio 'nun DE [Setresponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) çağrısını iletişim kurması gerekir. Örneğin, bu, bunun ileti işleme iş parçacığına postalanan bir ileti ile yapılabilir veya bu arabirimi uygulayan nesne DE DE bir başvuru tutabilir ve buna geçilen Yanıt ile geri çağrı yapabilir `IDebugMessageEvent2::SetResponse` .

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE, bir yanıt gerektiren kullanıcıya bir ileti göstermek için bu olay nesnesini oluşturur ve gönderir. Olay, ayıklanmakta olan programa eklendiği zaman SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) callback işlevi kullanılarak gönderilir.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugMessageEvent2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Görüntülenecek iletiyi alır.|
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|İleti kutusundan yanıtı (varsa) ayarlar.|

## <a name="remarks"></a>Açıklamalar
 Ayrıca, kullanıcıdan belirli bir ileti için belirli bir yanıt gerekiyorsa bu arabirimi kullanır. Örneğin, bir programa uzaktan iliştirme denemesinden sonra da "erişim reddedildi" iletisi alırsa, bu özel iletiyi ileti kutusu stiliyle bir olayda Visual Studio 'ya gönderir `IDebugMessageEvent2` `MB_RETRYCANCEL` . Bu, kullanıcının iliştirme işlemini yeniden denemesini veya iptal etmesine olanak tanır.

 Ayrıca, bu iletinin Win32 işlevinin kurallarını izleyerek nasıl işleneceğini belirtir `MessageBox` (Ayrıntılar için bkz. [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) ).

 Visual Studio 'ya kullanıcıdan yanıt gerektirmeyen iletiler göndermek için [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) arabirimini kullanın.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
