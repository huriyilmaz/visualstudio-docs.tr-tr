---
description: Bu arabirim, hata ayıklama altyapısı (DE) tarafından kullanıcıdan yanıt Visual Studio bir ileti göndermek için kullanılır.
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
ms.openlocfilehash: 21bd32714b9f10174a1ebd3c2ad82dda16db715f9600318bd391f0c99e036463
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121307329"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
Bu arabirim, hata ayıklama altyapısı (DE) tarafından kullanıcıdan yanıt Visual Studio bir ileti göndermek için kullanılır.

## <a name="syntax"></a>Syntax

```
IDebugMessageEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE, kullanıcı yanıtı gerektiren bir ileti göndermek Visual Studio arabirimini uygulamaya alır. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi, bu arabirimle aynı nesne üzerinde uygulanarak uygulanarak. SDM, [arabirime erişmek için QueryInterface](/cpp/atl/queryinterface) `IDebugEvent2` kullanır.

 Bu arabirimin uygulanması, Visual Studio De'ye [SetResponse çağrısıyla](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) iletişim kurması gerekir. Örneğin, bu işlem DE'nin ileti işleme iş parçacığına gönderilen bir iletiyle yapılabilir veya bu arabirimi uygulayan nesne DE'ye bir başvuru tutabilir ve içine geçirilen yanıtla DE'ye geri `IDebugMessageEvent2::SetResponse` çağırabilirsiniz.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE, kullanıcıya yanıt gerektiren bir ileti görüntülemek için bu olay nesnesini oluşturur ve gönderir. Olay, hata ayıklama yapılan programa ekli olduğunda SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) geri çağırma işlevi kullanılarak gönderilir.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugMessageEvent2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Görüntülenecek iletiyi alır.|
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|İleti kutusundan yanıtı (varsa) ayarlar.|

## <a name="remarks"></a>Açıklamalar
 DE, belirli bir ileti için kullanıcıdan belirli bir yanıt gerektiriyorsa bu arabirimi kullanır. Örneğin, DE bir programa uzaktan ekleme girişiminden sonra bir "Erişim Reddedildi" iletisi alıyorsa, DE bu iletiyi ileti kutusu stiline sahip bir olayda Visual Studio'ye `IDebugMessageEvent2` `MB_RETRYCANCEL` gönderir. Bu, kullanıcının ekleme işlemini yeniden denemesini veya iptalini sağlar.

 DE, bu iletinin Win32 işlevinin kurallarına uygun olarak nasıl `MessageBox` işlen olacağını belirtir (ayrıntılar için bkz. [AfxMessageBox).](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)

 [Kullanıcıdan yanıt gerektirmeyen IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) arabirimini Visual Studio ileti göndermek için kullanın.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
