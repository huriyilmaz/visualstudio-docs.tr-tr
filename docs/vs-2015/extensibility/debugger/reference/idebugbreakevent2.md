---
title: IDebugBreakEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 98e8c1b1669b3fdd1f442c6987e4e9d2b9fc4835
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675375"
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim, oturum hata ayıklama Yöneticisi 'ne (SDM) zaman uyumsuz bir kesmenin başarıyla tamamlandığını söyler.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugBreakEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Bu arabirimi, bir programdaki Kullanıcı sonlarını desteklemek için DE uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi bu arabirimle aynı nesne üzerinde UYGULANMALıDıR (SDM, arabirime erişmek için [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) kullanır `IDebugEvent2` ).  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Kullanıcı hata ayıklamakta olan programın duraklatılmasını istediği zaman SDM, [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) çağırır. Program başarıyla duraklatıldığında `IDebugBreakEvent2` olayı gönderir. Bu olay, hata ayıklamakta olan programa eklendiğinde SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) callback işlevi kullanılarak gönderilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Örneğin, bir Kullanıcı, sonsuz bir döngü çalıştıran bir programdan ayırmak için **hata ayıklama** menüsündeki **Tümünü kes** komutunu seçebilir. SDM, programa [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)çağırarak durmasını söyler. , `IDebugBreakEvent2` Program finally DURDURULDUĞUNDA de gönderir.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
