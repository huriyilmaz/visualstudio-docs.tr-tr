---
title: IDebugBeforeSymbolSearchEvent2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBeforeSymbolSearchEvent2 interface
ms.assetid: 679fd7b1-765a-41a8-a046-63240c09a499
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9d6f3f78e165ba2f4453131b7b459e3061243ff6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736116"
---
# <a name="idebugbeforesymbolsearchevent2"></a>IDebugBeforeSymbolSearchEvent2
Hata ayıklama altyapısı (DE), bu arabirimi, sembol yükleri sırasında durum çubuğu iletisini ayarlamak üzere oturum hata ayıklama yöneticisine (SDM) gönderir.

## <a name="syntax"></a>Sözdizimi

```
IDebugBeforeSymbolSearchEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE, sembol yükleri sırasında durum çubuğu iletisini ayarlaması gerektiğinde bu arabirimi uygular. Bu arabirim yalnızca komut dosyası yorumlayıcılarıyla çalışan veya bunların bir parçası olan hata ayıklama motorları tarafından uygulanır. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi bu arabirimle aynı nesne üzerinde uygulanmalıdır (SDM, **IDebugEvent2** arabirimine erişmek için **QueryInterface'i** kullanır).

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE, sembol yükleri sırasında durum çubuğu iletisini ayarlaması gerektiğinde bu olay nesnesini oluşturur ve gönderir. Olay, sdm tarafından sağlanan [iDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) geri arama işlevi kullanılarak, programa eklendiğinde debugged olarak gönderilir.

## <a name="methods"></a>Yöntemler
 Aşağıdaki tabloda `IDebugBeforeSymbolSearchEvent2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetModuleName](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2-getmodulename.md)|Şu anda debugged olan modülün adını alır.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: Msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll
