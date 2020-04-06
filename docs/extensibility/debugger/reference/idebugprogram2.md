---
title: IDebugProgram2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2
helpviewer_keywords:
- IDebugProgram2 interface
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 150746197be4945b012717bef08e18ea57168177
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722722"
---
# <a name="idebugprogram2"></a>IDebugProgram2
Bu arabirim, bir işlemde çalışan bir programı temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE) ve özel bir bağlantı noktası tedarikçisi, bir işlemdeki programı temsil etmek için bu arabirimi uygular. Oturum hata ayıklama yöneticisi (SDM) de [ekle'ye](../../../extensibility/debugger/reference/idebugprogram2-attach.md)bilgi sağlamak için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) etkinliği yeni bir program için bu arabirimi döndürür. Bu arabirim aynı zamanda birden çok arabirimdeki birçok yöntem için bir parametre olarak da kullanılır.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugProgram2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|Bu programda çalışan iş parçacıklarını doğrular.|
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|Programın adını alır.|
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|Bu programın yürüttüğü işlemi alıyor.|
|[Terminate](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|Bu programı sona erdirir.|
|[İliştir](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|Bu programa iliştiriler.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|Hata ayıklama altyapısının (DE) programdan ayırıp çıkaramayacağına karar vetir.|
|[Ayır](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|Hata ayıklamayı bu programdan ayırır.|
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|Bu program için benzersiz bir tanımlayıcı alır.|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|Program özelliklerini alır.|
|[Yürütmek](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|Bu programı durmuş durumdaki bir durumdan çalıştırmaya devam ediyor. Önceki herhangi bir yürütme durumu temizlendi.|
|[Devam](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|Bu programı durmuş durumdaki bir durumdan çalıştırmaya devam ediyor. Önceki yürütme durumu korunur.|
|[Adım](../../../extensibility/debugger/reference/idebugprogram2-step.md)|Bir adım gerçekleştirir.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|Bu programın, iş parçacıklarından biri kodu çalıştırdığı bir sonraki kez yürütmeyi durdurmasını ister.|
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|Bu programı çalıştıran hata ayıklama altyapısının (DE) adını ve tanımlayıcısını alır.|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|Kaynak dosyadaki belirli bir konumun kod bağlamlarını oyalar.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|Bu program için bellek bayt alır.|
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|Bu program veya bu programın bir parçası için sökme akışını alır.|
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|Bu programın yüklediği ve yürütüldettiği modülleri oyalar.|
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|Bu program için Edit ve Continue (ENC) güncelleştirmesini alır.<br /><br /> Özel hata ayıklama altyapısı bu yöntemi uygulamaz `E_NOTIMPL`(her zaman döndürülmelidir).|
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|Bu programın kod yollarını oyalar.|
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|Dosyaya bir döküm yazar.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Açıklamalar
 Bir işlem bir veya daha fazla programdan oluşurken, program belirli bir çalışma zamanı mimarisinde çalışan bir iş parçacığı kapsayıcısa.

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [Sonraki](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [Olay](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [İliştir](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
