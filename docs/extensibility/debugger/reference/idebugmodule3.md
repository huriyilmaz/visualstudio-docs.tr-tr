---
description: Bu arabirim, simgelerin alternatif konumlarını destekleyen bir modülü temsil eder ve kodu belirtir.
title: IDebugModule3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3
helpviewer_keywords:
- IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 38ced8edcc97ad4ab8ff4db430cea57a2533cb30
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149892"
---
# <a name="idebugmodule3"></a>IDebugModule3
Bu arabirim, simgelerin alternatif konumlarını destekleyen bir modülü temsil eder ve kodu belirtir.

## <a name="syntax"></a>Syntax

```
IDebugModule3 : IDebugModule2
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Hata ayıklama altyapısı (DE), bu arabirimi, simgelerin alternatif konumlarını desteklemek ve izin vermek MyCode durumlarıyla çalışmak için uygular ("Adatmycode" tanımı için [Visual Studio hata ayıklayıcı sözlüğü](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) ' ne bakın).

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) çağrısı bu arabirimi döndürür. DE, [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) arabirimini [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) metodunu kullanarak oturum hata ayıklama Yöneticisi 'ne (SDM) gönderir. Ayrıca, bir [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) arabirimindeki [QueryInterface](/cpp/atl/queryinterface) çağrısı bu arabirimi döndürür.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) arabirimindeki yöntemlere ek olarak, bu arabirim aşağıdaki yöntemleri uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|Simgeler için aranan yolların ve her bir yolu aramanın sonuçlarının listesini döndürür.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|Geçerli modül için sembolleri yükler ve başlatır.|
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|Modülün Kullanıcı kodunu temsil edip etmediğini belirten bayrağı döndürür.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|Modülün Kullanıcı kodu olarak kabul edilip edilmeyeceğini belirtir.|

## <a name="remarks"></a>Açıklamalar
 Visual Studio, bu arabirimin tipik tüketicisidir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
- [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)
