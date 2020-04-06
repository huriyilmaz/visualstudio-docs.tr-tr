---
title: İDebugModülü3 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3
helpviewer_keywords:
- IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84db1b672a9460ef3809162a2a1433f269796046
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726734"
---
# <a name="idebugmodule3"></a>IDebugModule3
Bu arabirim, sembollerin ve JustMyCode durumlarının alternatif konumlarını destekleyen bir modülü temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugModule3 : IDebugModule2
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE) bu arabirimi, sembollerin alternatif konumlarını desteklemek ve JustMyCode durumlarıyla çalışmak için uygular ("JustMyCode" tanımı için [Visual Studio Hata Ayıklama Sözlüğü'ne](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) bakın).

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) için bir çağrı bu arabirimi döndürür. DE, [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) yöntemini kullanarak oturum hata ayıklama yöneticisine (SDM) [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) arabirimini gönderir. Ayrıca, [Bir IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) arabiriminde [QueryInterface](/cpp/atl/queryinterface) için bir çağrı bu arabirimi döndürür.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) arabirimindeki yöntemlere ek olarak, bu arabirim aşağıdaki yöntemleri uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|Semboller için aranan yolların listesini ve her yolu aramanın sonuçlarını döndürür.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|Geçerli modül için semboller yükler ve başharfler.|
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|Modülün kullanıcı kodunu temsil edip etmediğini belirten bayrak döndürür.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|Modülün kullanıcı kodu olarak kabul edilip edilmemesi gerektiğini belirtir.|

## <a name="remarks"></a>Açıklamalar
 Visual Studio bu arabirimin tipik tüketicisidir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
- [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)
