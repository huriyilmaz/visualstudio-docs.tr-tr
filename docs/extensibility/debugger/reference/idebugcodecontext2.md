---
title: IDebugCodeContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f03bef276d4f4aada1a173c45defd100e4becbf4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928698"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
Bu arabirim, bir kod yönergesinin başlangıç konumunu temsil eder. Günümüzde çoğu çalışma zamanı mimarilerinde, bir programın yürütme akışında bir adres olarak bir kod bağlamı düşünülebilir.

## <a name="syntax"></a>Syntax

```
IDebugCodeContext2 : IDebugMemoryContext2
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Hata ayıklama altyapısı, bir kod yönergesinin konumunu bir belge konumuna ilişkilendirmek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Birçok arabirimdeki Yöntemler bu arabirimi, genellikle [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)' i döndürür. Ayrıca, [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) arabirimi ve kesme noktası çözümleme bilgileri ile de kapsamlı bir şekilde kullanılır.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) arabirimindeki yöntemlere ek olarak, bu arabirim aşağıdaki yöntemleri uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Etkin kod bağlamına karşılık gelen belge bağlamını alır.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Bu kod bağlamı için dil bilgisini alır.|

## <a name="remarks"></a>Açıklamalar
 Bir `IDebugCodeContext2` arabirim ve bir [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) arabirimi arasındaki temel fark, `IDebugCodeContext2` her zaman yönerge hizalı olur. Yani, bir `IDebugCodeContext2` yönergenin başlangıcını her zaman işaret eder, ancak `IDebugMemoryContext2` çalışma zamanı mimarisinde herhangi bir bellek baytına işaret edebilir. `IDebugCodeContext2` temel depolama boyutu (genellikle bayt) yerine yönergelerle artırılır.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)
- [Sonraki](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
