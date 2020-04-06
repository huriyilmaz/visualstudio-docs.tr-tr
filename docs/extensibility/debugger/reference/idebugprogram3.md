---
title: IDebugProgram3 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3 interface
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9da63d54f64a4ef7592fdbc4d36e2b31220f82df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722649"
---
# <a name="idebugprogram3"></a>IDebugProgram3
Bu arabirim, bir işlemde çalışan bir programı temsil eder ve iş parçacığı bilgileri sağlayarak [Execute'ı](../../../extensibility/debugger/reference/idebugprogram2-execute.md) genişletir.

## <a name="syntax"></a>Sözdizimi

```
IDebugProgram3 : IDebugProgram3
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE) ve özel bir bağlantı noktası tedarikçisi, bir işlemdeki programı temsil etmek için bu arabirimi uygular. Oturum hata ayıklama yöneticisi (SDM) de [ekle'ye](../../../extensibility/debugger/reference/idebugprogram2-attach.md)bilgi sağlamak için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) etkinliği yeni bir program için bu arabirimi döndürür. Bu arabirim aynı zamanda birden çok arabirimdeki birçok yöntem için bir parametre olarak da kullanılır.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugProgram3`.

|Yöntem|Açıklama|
|------------|-----------------|
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|Programı yürütür. İş parçacığı, kullanıcının yürüterken görüntülediği iş parçacığı hakkında hata ayıklama bilgileri vermek için döndürülür.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Açıklamalar
 Bir işlem bir veya daha fazla programdan oluşurken, program belirli bir çalışma zamanı mimarisinde çalışan bir iş parçacığı kapsayıcısa.

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
