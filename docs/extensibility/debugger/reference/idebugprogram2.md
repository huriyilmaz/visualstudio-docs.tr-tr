---
description: Bu arabirim, bir işlemde çalışan bir programı temsil eder.
title: IDebugProgram2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2
helpviewer_keywords:
- IDebugProgram2 interface
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 4ada2036c6ae2f82066d6ed12344dc1f301c54d7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122087775"
---
# <a name="idebugprogram2"></a>IDebugProgram2
Bu arabirim, bir işlemde çalışan bir programı temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE) ve özel bir bağlantı noktası sağlayıcı, bir süreci bir programı temsil etmek için bu arabirimi benimser. Oturum hata ayıklama yöneticisi (SDM), Attach 'e bilgi sağlamak için bu arabirimi de [uygulamaya ekler.](../../../extensibility/debugger/reference/idebugprogram2-attach.md)

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [IDebugProgramCreateEvent2 olayı](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) yeni bir program için bu arabirimi döndürür. Bu arabirim, birden çok arabirimde birçok yöntem için parametre olarak da kullanılır.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugProgram2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|Bu programda çalışan iş parçacıklarını numaralar.|
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|Programın adını alır.|
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|Bu programın içinde çalıştır olduğu işlemi alır.|
|[Terminate](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|Bu programı sonlandırılır.|
|[İliştir](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|Bu programa iliştirer.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|Bir hata ayıklama altyapısının (DE) programdan ayrılabilir olup olmadığını belirler.|
|[Ayır](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|Hata ayıklayıcıyı bu programdan ayırır.|
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|Bu program için genel olarak benzersiz bir tanımlayıcı alır.|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|Program özelliklerini alır.|
|[Yürütme](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|Bu programı durdurulmuş durumdan çalıştırmaya devam eder. Önceki yürütme durumu temiz.|
|[Devam et](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|Bu programı durdurulmuş durumdan çalıştırmaya devam eder. Önceki yürütme durumu korunur.|
|[Adım](../../../extensibility/debugger/reference/idebugprogram2-step.md)|Bir adım gerçekleştirir.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|İş parçacıklarının biri kod çalıştıracaksa bu programın yürütmeyi durdurmasını talep ediyor.|
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|Bu programı çalıştıran hata ayıklama altyapısının (DE) adını ve tanımlayıcısını alır.|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|Kaynak dosyada verilen bir konum için kod bağlamlarını numaralar.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|Bu programın bellek baytlarını alır.|
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|Bu program veya bu programın bir parçası için ayrım akışını alır.|
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|Bu programın yüklemiş ve yürütülmektedir modüllerini numaralar.|
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|Bu program için Düzenle ve Devam (ENC) güncelleştirmesini alır.<br /><br /> Özel hata ayıklama altyapısı bu yöntemi uygulamaz (her zaman dönüş `E_NOTIMPL` yapar).|
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|Bu programın kod yollarını numaralar.|
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|Bir dosyaya döküm yazar.|

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Açıklamalar
 Program, belirli bir çalışma zamanı mimarisinde çalışan bir iş parçacığı kapsayıcısı, bir işlem ise bir veya daha fazla programdan yapılır.

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [Sonraki](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [Olay](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [İliştir](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
