---
title: IDebugProgram2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2
helpviewer_keywords:
- IDebugProgram2 interface
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 372c119b6a841d7d4b349e85548914f7641b53d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148641"
---
# <a name="idebugprogram2"></a>IDebugProgram2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim, bir işlemde çalışan bir programı temsil eder.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProgram2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Hata ayıklama altyapısı (DE) ve özel bir bağlantı noktası sağlayıcısı, bu arabirimi bir işlem içindeki bir programı temsil etmek için uygular. Oturum hata ayıklama Yöneticisi (SDM), [iliştirilecek](../../../extensibility/debugger/reference/idebugprogram2-attach.md)bilgileri sağlamak için bu arabirimi de uygular.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) olayı yeni bir program için bu arabirimi döndürür. Bu arabirim, birden fazla arabirimde birçok yöntem için bir parametre olarak da kullanılır.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugProgram2` .  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|Bu programda çalışan iş parçacıklarını numaralandırır.|  
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|Programın adını alır.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|Bu programın üzerinde çalıştığı işlemi alır.|  
|[Terminate](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|Bu programı sonlandırır.|  
|[İliştir](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|Bu programa ekler.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|Bir hata ayıklama altyapısının (DE) programdan ayrılamayacağını belirler.|  
|[Ayır](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|Hata ayıklayıcıyı bu programdan ayırır.|  
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|Bu program için genel olarak benzersiz bir tanımlayıcı alır.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|Program özelliklerini alır.|  
|[Yürütme](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|Bu programı durdurulmuş bir durumdan çalıştırmaya devam eder. Önceki yürütme durumları temizlenir.|  
|[Devam et](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|Bu programı durdurulmuş bir durumdan çalıştırmaya devam eder. Önceki yürütme durumları korunur.|  
|[Adım](../../../extensibility/debugger/reference/idebugprogram2-step.md)|Bir adım gerçekleştirir.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|Bu programın iş parçacıklarından birinin kodu çalıştırması için bir dahaki sefer yürütmeyi durdurmasını ister.|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|Bu programı çalıştıran hata ayıklama altyapısının (DE) adını ve tanımlayıcısını alır.|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|Kaynak dosyadaki belirli bir konumun kod bağlamlarını numaralandırır.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|Bu program için bellek baytlarını alır.|  
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|Bu program veya bu programın bir parçası için ayrıştırma akışını alır.|  
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|Bu programın yüklediği ve yürütüldüğü modülleri numaralandırır.|  
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|Bu program için Düzenle ve devam et (ENC) güncelleştirmesini alır.<br /><br /> Özel bir hata ayıklama altyapısı bu yöntemi uygulamaz (her zaman döndürmelidir `E_NOTIMPL` ).|  
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|Bu programın kod yollarını numaralandırır.|  
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|Bir dosyaya döküm yazar.|  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Açıklamalar  
 Bir program, belirli bir çalışma zamanı mimarisinde çalışan bir iş parçacığı kapsayıcısıdır ve bir işlem bir veya daha fazla programdan oluşur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)   
 [İleri](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)   
 [Olay](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Ekleme](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Destroyıprogram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
