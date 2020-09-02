---
title: IDebugBreakpointRequest3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest3
helpviewer_keywords:
- IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 50ea30c736a4606a7745e52057f2ca8f9afd2c5f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65673772"
---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim, herhangi bir kesme noktası türü oluşturmak ve bağlamak için gereken bilgileri temsil eder. Bu bir [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)uzantısıdır.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugBreakpointRequest3 : IDebugBreakpointRequest2  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Oturum hata ayıklama Yöneticisi (SDM), bu arabirimi genellikle uygular.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Hata ayıklama altyapısı (DE), [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)çağrısında alınan IDebugBreakpointRequest2 arabirimine [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) çağırarak bu arabirime erişir.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)öğesinden devralınan yöntemlere ek olarak, `IDebugBreakpointRequest3` arabirimi aşağıdaki yöntemi kullanıma sunar.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|Bu kesme noktası isteğini açıklayan kesme noktası istek bilgilerini alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu arabirim, [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) yapısıyla aynı bilgilere ek bilgi sağlamak için kullanılır. Bu ek bilgiler, satıcı KIMLIĞINI (bir GUID biçiminde), izleneme noktasının adını ve bir kesme noktası kısıtlamasının adını içerir.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
