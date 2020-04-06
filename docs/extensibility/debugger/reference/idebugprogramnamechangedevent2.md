---
title: IDebugProgramNameChangedEvent2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramNameChangedEvent2 interface
ms.assetid: be1f1cd5-0b2f-435c-a052-dca28a7c978d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae58728601c3adbe6e37a00fd0694a5d71eef0b5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722155"
---
# <a name="idebugprogramnamechangedevent2"></a>IDebugProgramNameChangedEvent2
Bir programın adı değiştiğinde hata ayıklama altyapısından (DE) oturum hata ayıklama yöneticisine (SDM) gönderilir.

## <a name="syntax"></a>Sözdizimi

```
IDebugProgramNameChangedEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE, programın adının değiştiğini bildirmek için bu arabirimi uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi bu arabirimle aynı nesne üzerinde uygulanmalıdır. SDM, **IDebugEvent2** arabirimine erişmek için [QueryInterface'i](/cpp/atl/queryinterface) kullanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE, program adı değişikliğini bildirmek için bu olay nesnesini oluşturur ve gönderir. DE bu olayı, sdm tarafından verilen [iDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) geri arama işlevini kullanarak gönderir. Özel bağlantı noktası tedarikçisi bu olayı I arabirimini kullanarak gönderir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: Msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll
