---
title: DOCCONTEXT_COMPARE | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 75e4453cae63f484961cb2d0f3385a703709f83b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737234"
---
# <a name="doccontext_compare"></a>DOCCONTEXT_COMPARE
İki belge bağlamını karşılaştırmak için ölçütleri belirtir.

## <a name="syntax"></a>Sözdizimi

```cpp
enum enum_DOCCONTEXT_COMPARE {
    DOCCONTEXT_EQUAL         = 0x0001,
    DOCCONTEXT_LESS_THAN     = 0x0002,
    DOCCONTEXT_GREATER_THAN  = 0x0003,
    DOCCONTEXT_SAME_DOCUMENT = 0x0004
};
typedef DWORD DOCCONTEXT_COMPARE;
```

```csharp
enum enum_DOCCONTEXT_COMPARE {
    DOCCONTEXT_EQUAL         = 0x0001,
    DOCCONTEXT_LESS_THAN     = 0x0002,
    DOCCONTEXT_GREATER_THAN  = 0x0003,
    DOCCONTEXT_SAME_DOCUMENT = 0x0004
};
```

## <a name="fields"></a>Alanlar
`DOCCONTEXT_EQUAL`\
Listedeki hedef belge bağlamına eşit olan ilk belge bağlamını bulun.

`DOCCONTEXT_LESS_THAN`\
Listedeki hedef belge bağlamından daha az olan ilk belge bağlamını bulun.

`DOCCONTEXT_GREATER_THAN`\
Listede hedef belge bağlamından büyük olan ilk belge bağlamını bulun.

`DOCCONTEXT_SAME_DOCUMENT`\
Hedef belge bağlamıyla aynı belgede bulunan listedeki ilk belge bağlamını bulun.

## <a name="remarks"></a>Açıklamalar
[Karşılaştır](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) metoduna bağımsız değişken olarak geçirilir.

Bu değerler, bir listedeki ilk belge bağlamını bulmak için karşılaştırma ölçütleri belirtmek için kullanılır. Belge bağlamına, `IDebugDocumentContext2::Compare` yöntem aracılığıyla kendisini karşılaştırmak için belge bağlamlarının bir listesi verilir. Karşılaştırma işlecinin bulunduğu `true` listedeki ilk belge bağlamı döndürülür.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Karşılaştır](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)
