---
title: IDebugInterceptExceptionCompleteEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugInterceptExceptionCompleteEvent2
helpviewer_keywords:
- IDebugInterceptExceptionCompleteEvent2
ms.assetid: 8ebc256b-5428-4ed6-a505-6aedc8242b8e
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e617e7c19ae126980c0be5473fa279c0f69ff97a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690246"
---
# <a name="idebuginterceptexceptioncompleteevent2"></a>IDebugInterceptExceptionCompleteEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim, olay ayıklama altyapısı (DE) tarafından, iptal edilmiş bir olayın işlenmesini tamamladıktan sonra oturum hata ayıklama Yöneticisi 'ne (SDM) gönderilir.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugInterceptExceptionCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Bu arabirimi, ele alınmış bir özel durumun işlenmesini raporlamak için DE uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabiriminin bu arabirimle aynı nesne üzerinde uygulanması gerekir. SDM, arabirime erişmek için [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) kullanır `IDebugEvent2` .  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Aynı şekilde, ele alınamayan bir özel durumun tamamlanmasını raporlamak için bu olay nesnesini oluşturur ve gönderir. Olay, hata ayıklamakta olan programa eklendiğinde SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) callback işlevi kullanılarak gönderilir.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 `IDebugInterceptExceptionCompleteEvent2`Arabirimi aşağıdaki yöntemleri uygular.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetInterceptCookie](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2-getinterceptcookie.md)|İşlenmiş özel durumla ilişkili benzersiz değeri döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu olay, ele geçirilebilecek bir özel durumu işlemeyi başarıyla tamamladığında, bu olay [Yakatcurrentexception](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) tarafından gönderilir.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)   
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)
