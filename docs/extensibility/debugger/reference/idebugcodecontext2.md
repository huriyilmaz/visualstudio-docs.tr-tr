---
description: Bu arabirim, bir kod yönergesi başlangıç konumunu temsil eder.
title: IDebugCodeContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: da3fdc1c8f3c9c836519ba45d39df0aeca326d05
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122104137"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
Bu arabirim, bir kod yönergesi başlangıç konumunu temsil eder. Günümüzde çoğu çalışma zamanı mimarisinde kod bağlamı, bir programın yürütme akışındaki bir adres olarak düşünebilirsiniz.

## <a name="syntax"></a>Syntax

```
IDebugCodeContext2 : IDebugMemoryContext2
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı, bir kod yönergesi konumunu belge konumuyla ilişkilendirmek için bu arabirimi uygulamaya almaktadır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Birçok arabirimde kullanılan yöntemler, bu arabirimi genellikle [GetCodeContext olarak kullanır.](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) Ayrıca [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) arabirimi ve kesme noktası çözümleme bilgileriyle kapsamlı olarak kullanılır.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 [Bu arabirim, IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) arabiriminde yöntemlere ek olarak aşağıdaki yöntemleri de kullanır:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Etkin kod bağlamına karşılık gelen belge bağlamını alır.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Bu kod bağlamı için dil bilgilerini alır.|

## <a name="remarks"></a>Açıklamalar
 Arabirim ile `IDebugCodeContext2` [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) arabirimi arasındaki temel fark, bir arabiriminin her zaman `IDebugCodeContext2` yönergeyle hizalanmış olduğudur. Bu, bir her zaman bir yönergenin başlangıcına işaret ediyor, ancak bir çalışma zamanı mimarisinde herhangi bir bellek `IDebugCodeContext2` `IDebugMemoryContext2` baytı işaret ediyor olabilir. `IDebugCodeContext2` temel depolama boyutu (genellikle byte) yerine yönergelerle artırılır.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)
- [Sonraki](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
