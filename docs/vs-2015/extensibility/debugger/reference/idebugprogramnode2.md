---
title: IDebugProgramNode2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNode2
helpviewer_keywords:
- IDebugProgramNode2 interface
ms.assetid: 80e511d8-9b40-4a85-aa5d-952fa5ee6ae7
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1188f18e4a6f604dfd82991433bc0ffe0a07ad47
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148569"
---
# <a name="idebugprogramnode2"></a>IDebugProgramNode2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim, hata ayıklamanın bir programını temsil eder.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProgramNode2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Bir hata ayıklama altyapısı (DE) veya özel bir bağlantı noktası tedarikçisi, bu arabirimi, ayıklanabilecek bir programı temsil etmek için uygular. Bu arabirim, genellikle [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) arabirimini uygulayan aynı nesneye uygulanır. Bu arabirim, [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)çağırarak ile kaydedilir.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Bu arabirimi döndürmek için [Getproviderprogramnode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) öğesini çağırın. Özel bir bağlantı noktası sağlayıcısı bu arabirimi [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)çağrısıyla alır. Bu arabirimi [iliştirme](../../../extensibility/debugger/reference/idebugengine2-attach.md)çağrısıyla alır.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugProgramNode2` .  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetProgramName](../../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)|Bir programın adını alır.|  
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)|Bir programı barındıran işlemin adını alır.|  
|[GetHostPid](../../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)|Bir programı barındıran işlem için sistem işlem tanımlayıcısını alır.|  
|[GetHostMachineName_V7](../../../extensibility/debugger/reference/idebugprogramnode2-gethostmachinename-v7.md)|Kullanım dışı. KULLANMAYıN.|  
|[Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)|Kullanım dışı. KULLANMAYıN. Alternatif bir yaklaşım için bkz. [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) arabirimi.|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)|Bu programı çalıştıran öğesinin adını ve tanımlayıcısını alır.|  
|[DetachDebugger_V7](../../../extensibility/debugger/reference/idebugprogramnode2-detachdebugger-v7.md)|Kullanım dışı. KULLANMAYıN.|  
  
## <a name="remarks"></a>Açıklamalar  
 Oturum hata ayıklama Yöneticisi (SDM), bu arabirimi edinmek için genellikle [Getproviderprogramnode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) yöntemini çağırır.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)   
 [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)   
 [Ekleme](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)   
 [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)
