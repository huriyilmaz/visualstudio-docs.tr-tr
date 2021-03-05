---
description: Hata ayıklama altyapısı (DE), sembol yüklemeleri sırasında durum çubuğu iletisini ayarlamak için bu arayüzü oturum hata ayıklama Yöneticisi 'ne (SDM) gönderir.
title: IDebugBeforeSymbolSearchEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBeforeSymbolSearchEvent2 interface
ms.assetid: 679fd7b1-765a-41a8-a046-63240c09a499
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fdf292a309e514f5b437b129bbfc6ee125df8269
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167743"
---
# <a name="idebugbeforesymbolsearchevent2"></a>IDebugBeforeSymbolSearchEvent2
Hata ayıklama altyapısı (DE), sembol yüklemeleri sırasında durum çubuğu iletisini ayarlamak için bu arayüzü oturum hata ayıklama Yöneticisi 'ne (SDM) gönderir.

## <a name="syntax"></a>Syntax

```
IDebugBeforeSymbolSearchEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bu arabirim, sembol yüklemeleri sırasında durum çubuğu iletisini ayarlaması gerektiğinde DE uygular. Bu arabirim yalnızca ile çalışan veya betik yorumlayıcılarının bir parçası olan hata ayıklama motorları tarafından uygulanır. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabiriminin bu arabirimle aynı nesne üzerinde uygulanması gerekır (SDM, **IDebugEvent2** arabirimine erişmek için **QueryInterface** kullanır).

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE, sembol yüklemeleri sırasında durum çubuğu iletisini ayarlaması gerektiğinde bu olay nesnesini oluşturur ve gönderir. Olay, hata ayıklamakta olan programa eklendiğinde SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) callback işlevi kullanılarak gönderilir.

## <a name="methods"></a>Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugBeforeSymbolSearchEvent2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetModuleName](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2-getmodulename.md)|Şu anda hata ayıklanan modülün adını alır.|

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll
