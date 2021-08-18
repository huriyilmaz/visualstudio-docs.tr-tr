---
description: Bu arabirim sembollerin ve JustMyCode durumlarının alternatif konumlarını destekleyen bir modülü temsil eder.
title: IDebugModule3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3
helpviewer_keywords:
- IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 11b6db77e947ae8cb2ace6353b3f55aa8db48664
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122078849"
---
# <a name="idebugmodule3"></a>IDebugModule3
Bu arabirim sembollerin ve JustMyCode durumlarının alternatif konumlarını destekleyen bir modülü temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugModule3 : IDebugModule2
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE), sembollerin alternatif konumlarını desteklemek ve JustMyCode durumları ile çalışmak için bu arabirimi (bkz. "JustMyCode" tanımı için [Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) Hata Ayıklayıcısı Sözlüğü).

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [GetSymbolSearchInfo çağrısı bu](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) arabirimi döndürür. DE, Event yöntemini [kullanarak IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) arabirimini oturum hata ayıklama yöneticisine (SDM) [gönderir.](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) Ayrıca, [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) [arabiriminde QueryInterface](/cpp/atl/queryinterface) çağrısı bu arabirimi döndürür.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 [Bu arabirim, IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) arabiriminde yöntemlere ek olarak aşağıdaki yöntemleri de kullanır:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|Semboller için arama yapılan yolların listesini ve her bir yolu arama sonuçlarını döndürür.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|Geçerli modül için sembolleri yükler ve başlatılır.|
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|Modülün kullanıcı kodunu temsil edip ettiğini belirten bayrağı döndürür.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|Modülün kullanıcı kodu olarak kabul edilir mi yoksa değil mi olacağını belirtir.|

## <a name="remarks"></a>Açıklamalar
 Visual Studio, bu arabirimin tipik tüketicisidir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
- [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)
