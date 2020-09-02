---
title: IDebugModule3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugModule3
helpviewer_keywords:
- IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 326efe27ae35de1550ebc8230ab3c94229589640
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690951"
---
# <a name="idebugmodule3"></a>IDebugModule3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim, simgelerin alternatif konumlarını destekleyen bir modülü temsil eder ve kodu belirtir.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugModule3 : IDebugModule2  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Hata ayıklama altyapısı (DE), bu arabirimi, simgelerin alternatif konumlarını desteklemek ve izin vermek MyCode durumlarıyla çalışmak için uygular ("Adatmycode" tanımı için [Visual Studio hata ayıklayıcı sözlüğü](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) ' ne bakın).  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) çağrısı bu arabirimi döndürür. DE, [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) arabirimini [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) metodunu kullanarak oturum hata ayıklama Yöneticisi 'ne (SDM) gönderir. Ayrıca, bir [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) arabirimindeki [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) çağrısı bu arabirimi döndürür.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) arabirimindeki yöntemlere ek olarak, bu arabirim aşağıdaki yöntemleri uygular:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|Simgeler için aranan yolların ve her bir yolu aramanın sonuçlarının listesini döndürür.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|Geçerli modül için sembolleri yükler ve başlatır.|  
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|Modülün Kullanıcı kodunu temsil edip etmediğini belirten bayrağı döndürür.|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|Modülün Kullanıcı kodu olarak kabul edilip edilmeyeceğini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Visual Studio, bu arabirimin tipik tüketicisidir.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)   
 [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)
