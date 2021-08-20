---
description: Bu arabirim, bir işlemde çalışan ve iş parçacığı bilgileri sağlayarak yürütmeyi genişleten bir programı temsil eder.
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
ms.openlocfilehash: 14a7641542bb5392c4e8eba1196059b5b8136948
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122159743"
---
# <a name="idebugprogram3"></a>IDebugProgram3
Bu arabirim, bir işlemde çalışan ve iş parçacığı bilgileri sağlayarak [yürütmeyi](../../../extensibility/debugger/reference/idebugprogram2-execute.md) genişleten bir programı temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugProgram3 : IDebugProgram3
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Hata ayıklama altyapısı (DE) ve özel bir bağlantı noktası sağlayıcısı, bu arabirimi bir işlem içindeki bir programı temsil etmek için uygular. Oturum hata ayıklama Yöneticisi (SDM), [iliştirilecek](../../../extensibility/debugger/reference/idebugprogram2-attach.md)bilgileri sağlamak için bu arabirimi de uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) olayı yeni bir program için bu arabirimi döndürür. Bu arabirim, birden fazla arabirimde birçok yöntem için bir parametre olarak da kullanılır.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugProgram3` .

|Yöntem|Açıklama|
|------------|-----------------|
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|Programı yürütür. İş parçacığı, çalıştırıldığında kullanıcı tarafından hangi iş parçacığının görüntülemekte olduğunu hata ayıklayıcı bilgilerini vermek üzere döndürülür.|

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Açıklamalar
 Bir program, belirli bir çalışma zamanı mimarisinde çalışan bir iş parçacığı kapsayıcısıdır ve bir işlem bir veya daha fazla programdan oluşur.

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
