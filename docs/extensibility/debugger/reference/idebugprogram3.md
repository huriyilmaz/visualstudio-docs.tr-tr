---
description: Bu arabirim, bir işlemde çalışan bir programı temsil eder ve iş parçacığı bilgilerini sağlayarak Yürütme'yi genişletmektedir.
title: IDebugProgram3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3 interface
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 8e1de2b61e7a942853cd0bae0d5526820030a4701921482a4aeb979cbfe96a2d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121338832"
---
# <a name="idebugprogram3"></a>IDebugProgram3
Bu arabirim, bir işlemde çalışan bir programı temsil eder ve iş parçacığı bilgilerini [sağlayarak Yürütme'yi](../../../extensibility/debugger/reference/idebugprogram2-execute.md) genişletmektedir.

## <a name="syntax"></a>Syntax

```
IDebugProgram3 : IDebugProgram3
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE) ve özel bir bağlantı noktası sağlayıcı, bir süreci bir programı temsil etmek için bu arabirimi benimser. Oturum hata ayıklama yöneticisi (SDM), Attach 'e bilgi sağlamak için bu arabirimi de [uygulamaya almaktadır.](../../../extensibility/debugger/reference/idebugprogram2-attach.md)

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [IDebugProgramCreateEvent2 olayı](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) yeni bir program için bu arabirimi döndürür. Bu arabirim, birden çok arabirimde birçok yöntem için parametre olarak da kullanılır.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugProgram3` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|Programı yürütür. İş parçacığı, hata ayıklayıcıya yürütürken kullanıcının hangi iş parçacığını görüntüle ilgili bilgi vermek için döndürülür.|

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Açıklamalar
 Program, belirli bir çalışma zamanı mimarisinde çalışan bir iş parçacığı kapsayıcısı, bir işlem ise bir veya daha fazla programdan yapılır.

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [Sonraki](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [Olay](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [İliştir](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
