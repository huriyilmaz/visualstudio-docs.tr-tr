---
title: IDebugCodeContext2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 778602cc29049d855c418fd8fa416feb1ad8e9fe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734215"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
Bu arabirim, kod yönergesinin başlangıç konumunu temsil eder. Günümüzde çoğu çalışma zamanı mimarisi için, kod bağlamı bir programın yürütme akışında bir adres olarak düşünülebilir.

## <a name="syntax"></a>Sözdizimi

```
IDebugCodeContext2 : IDebugMemoryContext2
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı, kod yönergesinin konumunu belge konumuyla ilişkilendirmek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Birçok arabirimdeki yöntemler, en tipik olarak [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)bu arabirimi döndürebilir. Ayrıca [iDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) arabirimi yanı sıra kesme noktası çözünürlük bilgileri ile yoğun olarak kullanılır.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) arabirimindeki yöntemlere ek olarak, bu arabirim aşağıdaki yöntemleri uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Etkin kod bağlamına karşılık gelen belge bağlamını alır.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Bu kod bağlamı için dil bilgilerini alır.|

## <a name="remarks"></a>Açıklamalar
 Arabirim `IDebugCodeContext2` ile [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) arabirimi arasındaki temel `IDebugCodeContext2` fark, bir arabirimin her zaman talimatla hizalanmış olmasıdır. Bu, bir `IDebugCodeContext2` talimatın başlangıcını her zaman işaret `IDebugMemoryContext2` ederken, çalışma zamanı mimarisindeki herhangi bir bellek baytına işaret edebilir anlamına gelir. `IDebugCodeContext2`temel depolama boyutu (genellikle bayt) yerine talimatlarla artarak elde edilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)
- [Sonraki](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
