---
description: Bir programın adı değiştiğinde, hata ayıklama altyapısından (DE) oturum hata ayıklama Yöneticisi 'ne (SDM) gönderilir.
title: IDebugProgramNameChangedEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramNameChangedEvent2 interface
ms.assetid: be1f1cd5-0b2f-435c-a052-dca28a7c978d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 60fbc8aac3fd621a8f19074682bd82fbe957ed3b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053704"
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
