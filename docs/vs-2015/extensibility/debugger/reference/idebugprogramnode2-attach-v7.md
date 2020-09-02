---
title: 'IDebugProgramNode2:: Attach_V7 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
ms.assetid: b5ffc736-efc7-4ca8-964d-5536ff891b0e
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 08028f2b03f3ea36cc72172ca8f9de31740b49f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64784993"
---
# <a name="idebugprogramnode2attach_v7"></a>IDebugProgramNode2::Attach_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Kullanım dışı. KULLANMAYıN.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT Attach_V7 (   
   IDebugProgram2*       pMDMProgram,  
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason  
);  
```  
  
```csharp  
int Attach_V7 (   
   IDebugProgram2       pMDMProgram,  
   IDebugEventCallback2 pCallback,  
   uint                 dwReason  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pMDMProgram`  
 'ndaki Eklenecek programı temsil eden [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) arabirimi.  
  
 `pCallback`  
 'ndaki Hata ayıklama olaylarını SDM 'ye göndermek için kullanılacak [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) arabirimi.  
  
 `dwReason`  
 'ndaki Ekleme nedeninizi belirten [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) numaralandırmasından bir değer.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir uygulama her zaman döndürmelidir `E_NOTIMPL` .  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!WARNING]
> İtibariyle [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] , bu yöntem artık kullanılmamaktadır ve her zaman döndürmelidir `E_NOTIMPL` . Program düğümünün, program düğümü tarafından yalnızca program olarak ayarlanması gerektiğini belirtmesi gerekiyorsa alternatif bir yaklaşım için [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) arabirimine bakın `GUID` . Aksi takdirde, [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) metodunu uygulayın.  
  
## <a name="prior-to-visual-studio-2005"></a>Visual Studio 2005 öncesi  
 Bu yöntemin yalnızca, hata ayıklamakta olan programın adres alanında çalışması durumunda uygulanması gerekir. Aksi takdirde, bu yöntem döndürmelidir `S_FALSE` .  
  
 Bu yöntem çağrıldığında, [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) arabiriminin bu örneği için zaten gönderilmemiş ve [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) ve [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) olay NESNELERININ yanı sıra [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) Event nesnesini de göndermelidir. [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) olay nesnesi daha sonra parametresi ise gönderilir `dwReason` `ATTACH_REASON_LAUNCH` .  
  
 Aynı [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) olay nesnesi tarafından sağlanan [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) nesnesinde [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) yöntemini ÇAĞıRMALıDıR ve bu programın GUID 'ini `IDebugProgram2` de tarafından uygulanan nesne için örnek verilerinde depolaması gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Ekleme](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)   
 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
