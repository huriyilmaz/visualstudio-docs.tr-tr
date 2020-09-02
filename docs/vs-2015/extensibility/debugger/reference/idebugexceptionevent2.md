---
title: IDebugExceptionEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2
helpviewer_keywords:
- IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f364b6aa622bf9c7481d61e7646e955cebe00933
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695396"
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Hata ayıklama altyapısı (DE), yürütülmekte olan programda bir özel durum oluştuğunda bu arayüzü oturum hata ayıklama Yöneticisi 'ne (SDM) gönderir.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugExceptionEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Bu arabirim, hata ayıklamakta olan programda bir özel durumun oluştuğunu bildirmek için DE uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabiriminin bu arabirimle aynı nesne üzerinde uygulanması gerekir. SDM, arabirime erişmek için [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) kullanır `IDebugEvent2` .  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 DE, özel durum bildirmek için bu olay nesnesini oluşturur ve gönderir. Olay, hata ayıklamakta olan programa eklendiğinde SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) callback işlevi kullanılarak gönderilir.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugExceptionEvent2` .  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|Bu olayı tetikleyen özel durumla ilgili ayrıntılı bilgileri alır.|  
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|Bu olayı tetikleyen özel durum için okunabilir bir açıklama alır.|  
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|Hata ayıklama altyapısının (DE), yürütme devam ettiğinde hata ayıklamakta olan programa bu özel durumu geçirme seçeneğini destekleyip desteklemediğini belirler.|  
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|Yürütmenin devam ettiğinde veya özel durumun atıldığında hata ayıklamakta olan programa özel durumun geçirilip geçirilmeyeceğini belirtir.|  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Açıklamalar  
 Olayı göndermeden önce, bu özel durum olayının bir önceki [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)çağrısıyla birinci şans veya ikinci şans özel durumu belirlenip belirlenmediğini de denetler. İlk fırsat özel durumu olarak belirlendiyse, `IDebugExceptionEvent2` olay SDM 'ye gönderilir. Aksi takdirde, uygulama özel durumu işlemeye yönelik bir şans verir. Özel durum işleyicisi sağlanmazsa ve özel durum ikinci şans özel durumu olarak belirlendiyse, `IDebugExceptionEvent2` olay SDM 'ye gönderilir. Aksi takdirde, DE programın yürütülmesini sürdürür ve işletim sistemi veya çalışma zamanı özel durumu işler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
