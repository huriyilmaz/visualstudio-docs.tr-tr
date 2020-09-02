---
title: IDebugReturnValueEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugReturnValueEvent2
helpviewer_keywords:
- IDebugReturnValueEvent2
ms.assetid: 2daded43-e427-4fbb-a19e-f3834e3723af
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b3a6ece54b76d38891f99cc96afa52df72d7138a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65676411"
---
# <a name="idebugreturnvalueevent2"></a>IDebugReturnValueEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim, bir işlevin dışına veya sonuna kadar hata ayıklama altyapısı (DE) tarafından oturum hata ayıklama Yöneticisi 'ne (SDM) gönderilir.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugReturnValueEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Bu, bir veya daha fazla dönerek bir işlevden dönüş değerini raporlamak için bu arabirimi uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabiriminin bu arabirimle aynı nesne üzerinde uygulanması gerekir. SDM, arabirime erişmek için [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) kullanır `IDebugEvent2` .  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 DE, bir işlevin dönüş değerini raporlamak için bu olay nesnesini oluşturur ve gönderir. Olay, ayıklanmakta olan programa eklendiği zaman SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) callback işlevi kullanılarak gönderilir.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 Aşağıdaki tabloda, yöntemi gösterilmektedir `IDebugReturnValueEvent2` .  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md)|Bir işlevin dışına atlama sırasında döndürülen değeri alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 İşlev tarafından döndürülen değer [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md)çağırarak elde edilebilir. Döndürülen değer, **oto** penceresinde görünür.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
