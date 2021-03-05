---
description: Bir programın adı değiştiğinde, hata ayıklama altyapısından (DE) oturum hata ayıklama Yöneticisi 'ne (SDM) gönderilir.
title: IDebugProgramNameChangedEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramNameChangedEvent2 interface
ms.assetid: be1f1cd5-0b2f-435c-a052-dca28a7c978d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 408d564efe6b0cbd76d5bf6993fcc0113a299cb7
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145228"
---
# <a name="idebugprogramnamechangedevent2"></a>IDebugProgramNameChangedEvent2
Bir programın adı değiştiğinde, hata ayıklama altyapısından (DE) oturum hata ayıklama Yöneticisi 'ne (SDM) gönderilir.

## <a name="syntax"></a>Syntax

```
IDebugProgramNameChangedEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bu arabirimi, programın adının değiştiğini raporlamak için DE uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabiriminin bu arabirimle aynı nesne üzerinde uygulanması gerekir. SDM, **IDebugEvent2** arabirimine erişmek için [QueryInterface](/cpp/atl/queryinterface) kullanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE, bir program adı değişikliğini raporlamak için bu olay nesnesini oluşturur ve gönderir. Bu olayı, hata ayıklamakta olan programa eklendiğinde SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) callback işlevini kullanarak gönderir. Özel bağlantı noktası sağlayıcısı bu olayı ı arabirimini kullanarak gönderir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll
