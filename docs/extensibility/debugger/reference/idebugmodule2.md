---
description: Bu arabirim, dll gibi bir programın yürütülebilir birimi olan bir modülü temsil eder.
title: IDebugModule2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: fb0c3776a56f09d80fc62173555c98f83d7cd616
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122043303"
---
# <a name="idebugmodule2"></a>IDebugModule2
Bu arabirim, dll gibi bir programın yürütülebilir birimi olan bir modülü temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugModule2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE), bir modülü temsil etmek ve bu modülle ilgili bilgilere erişim sağlamak için bu arabirimi uygulamaya almaktadır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [GetModule çağrısı bu](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) arabirimi döndürür. DE, Event yöntemini [kullanarak IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) arabirimini oturum hata ayıklama yöneticisine (SDM) [gönderir.](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)

 Bu arabirim bir [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) yapısında da döndürülebiliyor [(EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)çağrısı tarafından döndürülür).

- [Ardından](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) bu arabirimi de döndürür ([EnumModules,](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) [IEnumDebugModules2 arabirimini](../../../extensibility/debugger/reference/ienumdebugmodules2.md) döndürür).

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugModule2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|Bu [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) açıklayan modülü alır.|
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|Eski. KULLANMAYIN. Bu modülün sembollerini yeniden yükleme.|

## <a name="remarks"></a>Açıklamalar
 Modül bilgileri **IDE'nin** Modüller penceresinde görüntülenebilir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
