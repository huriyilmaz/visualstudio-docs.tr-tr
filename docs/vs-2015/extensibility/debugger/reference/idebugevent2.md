---
title: IDebugEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f663be5910b342a6adba5da0b84d7e0d80cacc10
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695408"
---
# <a name="idebugevent2"></a>IDebugEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim, bir kesme noktasında durdurma gibi kritik hata ayıklama bilgilerini ve hata ayıklama iletisi gibi kritik olmayan bilgileri iletişim kurmak için kullanılır.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Hata ayıklama altyapısı (DE) ve özel bağlantı noktası sağlayıcısı, bu arabirimi diğer tüm olay arabirimleriyle aynı nesneye uygular.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) veya [olaya](../../../extensibility/debugger/reference/idebugportevents2-event.md)VERILEN arabirim kimliği (IID) bağımsız değişkenini kullanarak, oturum hata ayıklama Yöneticisi (SDM), [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) `IDebugEvent2` uygun olay arabirimini elde etmek için arabirimdeki QueryInterface 'i çağırır.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugEvent2` .  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Bu hata ayıklama olayının özniteliklerini alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)gibi daha özel olay arabirimleri, IDebugEvent2 arabiriminden türemez, ancak bunun yerine aynı nesne üzerinde ayrı bir arabirim olarak uygulanır `IDebugEvent2` .  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Olay](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
