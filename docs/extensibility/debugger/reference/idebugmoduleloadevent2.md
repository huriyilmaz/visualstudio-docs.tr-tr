---
title: IDebugModuleLoadEvent2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModuleLoadEvent2
helpviewer_keywords:
- IDebugModuleLoadEvent2 interface
ms.assetid: 7d26fb23-5d49-4ba7-b7c5-3aed4d7be81e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 06bb96d8a02ccc9299d43f28b4fbfa3fdb39acdc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726706"
---
# <a name="idebugmoduleloadevent2"></a>IDebugModuleLoadEvent2
Bu arabirim, hata ayıklama altyapısı (DE) tarafından bir modül yüklendiğinde veya boşaltıldığında oturum hata ayıklama yöneticisine (SDM) gönderilir.

## <a name="syntax"></a>Sözdizimi

```
IDebugModuleLoadEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE, bir modülün yüklendiğini veya boşaltıldığını bildirmek için bu arabirimi uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi bu arabirimle aynı nesne üzerinde uygulanmalıdır. SDM `IDebugEvent2` [arabirime](/cpp/atl/queryinterface) erişmek için QueryInterface kullanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE, bir modülün yüklendiğini veya boşaltıldığını bildirmek için bu olay nesnesini oluşturur ve gönderir. Olay, debugged olan programa iliştirildiğinde SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) geri arama işlevi kullanılarak gönderilir.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugModuleLoadEvent2`. yöntemini gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)|Yüklenen veya boşaltılan modülü alır.|

## <a name="remarks"></a>Açıklamalar
 Visual **Studio, Modüller** penceresini güncel tutmak için bu olayı kullanır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
