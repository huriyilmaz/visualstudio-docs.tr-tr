---
description: Bir programın adı değişirken hata ayıklama altyapısından (DE) oturum hata ayıklama yöneticisine (SDM) gönderilir.
title: IDebugProgramNameChangedEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramNameChangedEvent2 interface
ms.assetid: be1f1cd5-0b2f-435c-a052-dca28a7c978d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 196950b96375612b1e8a541b4ec7abdb78d3d21a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122030093"
---
# <a name="idebugprogramnamechangedevent2"></a>IDebugProgramNameChangedEvent2
Bir programın adı değişirken hata ayıklama altyapısından (DE) oturum hata ayıklama yöneticisine (SDM) gönderilir.

## <a name="syntax"></a>Syntax

```
IDebugProgramNameChangedEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE, programın adının değiştiğini rapor etmek için bu arabirimini uygulamaya almaktadır. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi, bu arabirimle aynı nesne üzerinde uygulanarak uygulanarak. SDM, **IDebugEvent2** arabirimine erişmek için [QueryInterface](/cpp/atl/queryinterface) kullanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE bu olay nesnesini oluşturur ve program adı değişikliğini rapor etmek için gönderir. DE, hata ayıklaması yapılan programa ekli olduğunda SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) geri çağırma işlevini kullanarak bu olayı gönderir. Özel bağlantı noktası sağlayıcı bu olayı I arabirimini kullanarak gönderir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: Msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll
