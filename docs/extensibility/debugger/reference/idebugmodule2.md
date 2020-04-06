---
title: İDebugModülü2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dbbea1b52133de41dd26f437aeba31a0eff5a50a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726914"
---
# <a name="idebugmodule2"></a>IDebugModule2
Bu arabirim, DLL gibi bir programın çalıştırılabilir bir birimini temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugModule2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE) bir modülü temsil etmek ve bu modül hakkındaki bilgilere erişim sağlamak için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) için bir çağrı bu arabirimi döndürür. DE, [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) yöntemini kullanarak oturum hata ayıklama yöneticisine (SDM) [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) arabirimini gönderir.

 Bu arabirim, [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) yapısında da döndürülebilir [(EnumFrameInfo'ya](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)yapılan bir çağrı yla döndürülür).

- [Sonraki](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) de bu arabirimi döndürür[(EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) arabirimini döndürür).

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugModule2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|Bu modülü açıklayan [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) alır.|
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|Eski. KULLANMAYıN. Bu modül için sembolleri yeniden yükler.|

## <a name="remarks"></a>Açıklamalar
 Modül bilgileri IDE'nin **Modüller** penceresinde görüntülenebilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
