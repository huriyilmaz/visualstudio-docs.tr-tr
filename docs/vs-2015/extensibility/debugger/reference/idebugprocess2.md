---
title: IDebugProcess2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 68f1693bbbda9bbf7622c2378799db4a342be7a5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187973"
---
# <a name="idebugprocess2"></a>IDebugProcess2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim, bağlantı noktası üzerinde çalışan bir işlemi temsil eder. Bağlantı noktası yerel bağlantı noktası ise, `IDebugProcess2` genellikle yerel makinedeki fiziksel bir işlemi temsil eder.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProcess2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Bu arabirim, programları bir grup olarak yönetmek için özel bir bağlantı noktası sağlayıcısı tarafından uygulanır. Bu arabirimin bağlantı noktası sağlayıcısı tarafından uygulanması gerekir.  
  
 Bir hata ayıklama altyapısı, [Launchaskıya alınmış](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)aracılığıyla bir programın başlatılmasını destekliyorsa bu arabirimi de uygular.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Bu arabirim öncelikle bu işlemde tanımlanan bir program grubuyla etkileşim kurmak için oturum hata ayıklama Yöneticisi (SDM) tarafından çağrılır.  
  
 Bu arabirimi almak için [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) veya [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md) çağrısı yapın. Bu arabirim, çağırarak da döndürülür `IDebugEngineLaunch2::LaunchSuspended` .  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugProcess2` .  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|İşlemin açıklamasını alır.|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Bu işlemde bulunan programları numaralandırır.|  
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|İşlemin başlığını, kolay adını veya dosya adını alır.|  
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Bu işlemin üzerinde çalıştığı bir makine sunucusunun örneğini alır.|  
|[Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|İşlemi sonlandırır.|  
|[İliştir](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|İşleme iliştirir.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|SDM 'nin işlemi ayırabileceğini belirler.|  
|[Ayır](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Hata ayıklayıcıyı işlemden ayırır.|  
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Sistem işlem tanımlayıcısını alır.|  
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Bu işlem için genel olarak benzersiz bir tanımlayıcı alır.|  
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> Kullanım DıŞı|İşlemde hata ayıklama yapan oturumun adını alır.<br /><br /> Kullanım dışı. HER zaman DÖNDÜRMELIDIR `E_NOTIMPL` .]|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|İşlemde çalışan iş parçacıklarını numaralandırır.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Bu işlemdeki kodu çalıştıran bir sonraki programın durdurulması ister.|  
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Bu işlemin üzerinde çalıştığı bağlantı noktasını alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `IDebugProcess2` veya daha fazla [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) arabirimi içerir.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)   
 [Launchaskıya alındı](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)   
 [İleri](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)   
 [Olay](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
