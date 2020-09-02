---
title: IDebugCanStopEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bc4ac1f3a8d9b470fbb3734f822601a7dce08a44
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696678"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim, oturum hata ayıklama Yöneticisi 'nin (SDM) geçerli kod konumunda durdurulup durdurulmayacağını sormak için kullanılır.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugCanStopEvent2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Hata ayıklama altyapısı (DE), kaynak kodu üzerinden adımlamayı desteklemek için bu arabirimi uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi bu arabirimle aynı nesne üzerinde UYGULANMALıDıR (SDM, arabirime erişmek için [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) kullanır `IDebugEvent2` ).  
  
 Bu arabirimin uygulanması için, SDM 'nin [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) çağrısını hata ayıklama altyapısına iletmesi gerekir. Örneğin, bu, hata ayıklama altyapısının ileti işleme iş parçacığına postalanan bir iletiyle yapılabilir veya bu arabirimi uygulayan nesne hata ayıklama altyapısına bir başvuru tutabilir ve geçirilen bayrak ile hata ayıklama altyapısına geri çağrı yapabilir `IDebugCanStopEvent2::CanStop` .  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Aynı zamanda, her seferinde yürütmeye devam etmesi istenir ve DE kod aracılığıyla adımla bu yöntem de gönderebilir. Bu olay, hata ayıklamakta olan programa eklendiğinde SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) callback işlevi kullanılarak gönderilir.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugCanStopEvent2` .  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Bu olayın nedenini alır.|  
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Hata ayıklamakta olan programın bu olayın konumunda durmasının gerekip gerekmediğini belirtir (ve durdurma nedenini açıklayan bir olay gönderin) veya yürütmeye devam edin.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Bu olayın konumunu açıklayan belge bağlamını alır.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Bu olayın konumunu açıklayan kod bağlamını alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu, Kullanıcı bir işleve bir işlev halinde gösterildiğinde ve bir hata ayıklama bilgisi yoksa veya hata ayıklama bilgileri bulursa ve bu konum için kaynak kodun görüntülenip görüntülenemediğini bilmez, bu arabirimi DE gönderir.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
