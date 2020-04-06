---
title: CONTEXT_COMPARE | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1c88b50644d1adda2dd0eaa3b74a828f9739d70b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737606"
---
# <a name="context_compare"></a>CONTEXT_COMPARE
İki bellek bağlamını karşılaştırmak için ölçütleri belirtir.

## <a name="syntax"></a>Sözdizimi

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
Listedeki ilk bellek bağlamını bul, hedef bellek bağlamından daha azdır.

`CONTEXT_GREATER_THAN`\
Listedeki hedef bellek bağlamından daha büyük olan ilk bellek bağlamını bulun.

`CONTEXT_LESS_THAN_OR_EQUAL`\
Listede, hedef bellek bağlamından daha az veya eşit olan ilk bellek bağlamını bulun.

`CONTEXT_GREATER_THAN_OR_EQUAL`\
Listede hedef bellek bağlamından büyük veya eşit olan ilk bellek bağlamını bulun.

`CONTEXT_SAME_SCOPE`\
Listedeki ilk bellek bağlamını hedef bellek bağlamıyla aynı kapsamda bulun.

`CONTEXT_SAME_FUNCTION`\
Hedef bellek kapsamıyla aynı işlevde olan listedeki ilk bellek bağlamını bulun.

`CONTEXT_SAME_MODULE`\
Hedef bellek bağlamıyla aynı modülde bulunan listedeki ilk bellek bağlamını bulun.

`CONTEXT_SAME_PROCESS`\
Hedef bellek bağlamıyla aynı işlemde olan listedeki ilk bellek bağlamını bulun.

## <a name="remarks"></a>Açıklamalar
[Karşılaştır](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) metoduna bağımsız değişken olarak geçirilir.

Bu değerler, belirtilen karşılaştırma ölçütlerini karşılayan bir listedeki ilk bellek bağlamını bulmak için kullanılır. Bellek bağlamı, `IDebugMemoryContext2::Compare` yöntem aracılığıyla kendisini karşılaştırmak için bellek bağlamlarının bir listesi verilir. Karşılaştırma işlecinin bulunduğu `true` listedeki ilk bellek bağlamı döndürülür.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Karşılaştır](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)
