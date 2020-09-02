---
title: IDebugEngine3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1e43da0b05062c6c7b1c4d3cfe771ff0b93f83a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195789"
---
# <a name="idebugengine3"></a>IDebugEngine3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bir veya daha fazla modülün hatalarını ayıklamayı denetleyen tek bir hata ayıklama altyapısını (DE) temsil eder.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugEngine3 : IDebugEngine2  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Bu arabirim, bir özel DE (sembolleri destekliyorsa), izin vermek MyCode durumunu etkinleştirmek için uygulanır. Bu arabirim, sembolleri destekliyorsa ve bu arabirimin tarafından uygulanması gerekir.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Bu arabirim, sembolleri yüklenecek konumlar için Kullanıcı seçeneklerini geçirmek üzere oturum hata ayıklama Yöneticisi (SDM) tarafından çağrılır. Ayrıca, örneklendirilir altyapının GUID 'sini ayarlamak için çağrılır (Bu GUID, altyapı kaydı zamanından alınan ölçümleri temel alır). SDM Ayrıca bu arabirimi çağırarak ve hata ayıklayıcı tarafından bilinen tüm özel durumları belirtilen bir duruma ayarlamak için çağırır.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)öğesinden devralınan yöntemlere ek olarak, `IDebugEngine3` arabirim aşağıdaki yöntemleri sunar.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|Aynı hata ayıklama sembolleri aramak için DE kullanacağı yolu veya yolları ayarlar.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|Henüz sembolleri yüklü olmayan tüm modüller için sembolleri yükler.|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|, ' In ' DE bir DE daha fazla bilgi sağlar.|  
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|Ölçülerden DE GUID 'ı ayarlar.|  
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|Şu anda bekleyen tüm özel durumları belirtilen bir duruma ayarlayın.|  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
