---
description: Bu arabirim, hata ayıklama altyapısı (DE) tarafından, hata ayıklama yapılmakta olan programdaki bir iş parçacığı adı değiştiğinde oturum hata ayıklama Yöneticisi 'ne (SDM) gönderilir.
title: IDebugThreadNameChangedEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThreadNameChangedEvent2
helpviewer_keywords:
- IDebugThreadNameChangedEvent2
ms.assetid: 34c1652e-f019-48ba-8b26-ace20f8a158c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 1409edc9270e7bd41295ef011a206e5fe1e96e9a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122126082"
---
# <a name="idebugthreadnamechangedevent2"></a>IDebugThreadNameChangedEvent2
Bu arabirim, hata ayıklama altyapısı (DE) tarafından, hata ayıklama yapılmakta olan programdaki bir iş parçacığı adı değiştiğinde oturum hata ayıklama Yöneticisi 'ne (SDM) gönderilir.

## <a name="syntax"></a>Syntax

```
IDebugThreadNameChangedEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bu, bir iş parçacığının adının değiştiğini raporlamak için DE bu arabirimi uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabiriminin bu arabirimle aynı nesne üzerinde uygulanması gerekir. SDM, arabirime erişmek için [QueryInterface](/cpp/atl/queryinterface) kullanır `IDebugEvent2` .

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE, bir iş parçacığının adının değiştiğini raporlamak için bu olay nesnesini oluşturur ve gönderir. Olay, ayıklanmakta olan programa eklendiği zaman SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) callback işlevi kullanılarak gönderilir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
