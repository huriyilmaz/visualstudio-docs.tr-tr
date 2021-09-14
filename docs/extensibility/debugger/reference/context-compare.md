---
description: İki bellek bağlamlarını karşılaştırma ölçütlerini belirtir.
title: CONTEXT_COMPARE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 49c8975a93d54d9138cbdcf510e7ee18d5bc55d2
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725306"
---
# <a name="context_compare"></a>CONTEXT_COMPARE
İki bellek bağlamlarını karşılaştırma ölçütlerini belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_CONTEXT_COMPARE {
    CONTEXT_EQUAL                 = 0x0001,
    CONTEXT_LESS_THAN             = 0x0002,
    CONTEXT_GREATER_THAN          = 0x0003,
    CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,
    CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,
    CONTEXT_SAME_SCOPE            = 0x0006,
    CONTEXT_SAME_FUNCTION         = 0x0007,
    CONTEXT_SAME_MODULE           = 0x0008,
    CONTEXT_SAME_PROCESS          = 0x0009
};
typedef DWORD CONTEXT_COMPARE;
```

```csharp
public enum enum_CONTEXT_COMPARE {
    CONTEXT_EQUAL                 = 0x0001,
    CONTEXT_LESS_THAN             = 0x0002,
    CONTEXT_GREATER_THAN          = 0x0003,
    CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,
    CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,
    CONTEXT_SAME_SCOPE            = 0x0006,
    CONTEXT_SAME_FUNCTION         = 0x0007,
    CONTEXT_SAME_MODULE           = 0x0008,
    CONTEXT_SAME_PROCESS          = 0x0009
};
```

## <a name="fields"></a>Alanlar
`CONTEXT_EQUAL`\
Listedeki hedef bellek bağlamına eşit olan ilk bellek bağlamını bulun.

`CONTEXT_LESS_THAN`\
Listede hedef bellek bağlamından daha az olan ilk bellek bağlamını bulun.

`CONTEXT_GREATER_THAN`\
Listede hedef bellek bağlamından daha büyük olan ilk bellek bağlamını bulun.

`CONTEXT_LESS_THAN_OR_EQUAL`\
Listede, hedef bellek bağlamından daha küçük veya ona eşit olan ilk bellek bağlamını bulun.

`CONTEXT_GREATER_THAN_OR_EQUAL`\
Listede, hedef bellek bağlamından daha büyük veya ona eşit olan ilk bellek bağlamını bulun.

`CONTEXT_SAME_SCOPE`\
Hedef bellek bağlamıyla aynı kapsamdaki listede bulunan ilk bellek bağlamını bulun.

`CONTEXT_SAME_FUNCTION`\
Hedef bellek kapsamıyla aynı işlevde bulunan listedeki ilk bellek bağlamını bulun.

`CONTEXT_SAME_MODULE`\
Listede, hedef bellek içeriğiyle aynı modülde olan ilk bellek bağlamını bulun.

`CONTEXT_SAME_PROCESS`\
Listede, hedef bellek içeriğiyle aynı işlemde olan ilk bellek bağlamını bulun.

## <a name="remarks"></a>Açıklamalar
[Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) metoduna bir bağımsız değişken olarak geçirilir.

Bu değerler, belirtilen karşılaştırma ölçütlerini karşılayan bir listedeki ilk bellek bağlamını bulmak için kullanılır. Bellek bağlamına, yöntemi aracılığıyla kendisini karşılaştırmak için bellek bağlamlarının bir listesi verilir `IDebugMemoryContext2::Compare` . Karşılaştırma işlecinin daha sonra döndürüldüğü listedeki ilk bellek bağlamı `true` döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Karşılaştır](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)
