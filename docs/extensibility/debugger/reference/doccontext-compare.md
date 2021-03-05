---
description: İki belge içeriğini karşılaştırma ölçütlerini belirtir.
title: DOCCONTEXT_COMPARE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f64e2e8ec365daa84cbd1d4f7e3e9bdc43391d5e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170438"
---
# <a name="doccontext_compare"></a>DOCCONTEXT_COMPARE
İki belge içeriğini karşılaştırma ölçütlerini belirtir.

## <a name="syntax"></a>Syntax

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
Listede hedef belge bağlamından daha az olan ilk belge bağlamını bulun.

`DOCCONTEXT_GREATER_THAN`\
Listede hedef belge bağlamından daha büyük olan ilk belge bağlamını bulun.

`DOCCONTEXT_SAME_DOCUMENT`\
Hedef belge bağlamıyla aynı belgede bulunan listedeki ilk belge bağlamını bulun.

## <a name="remarks"></a>Açıklamalar
[Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) metoduna bir bağımsız değişken olarak geçirilir.

Bu değerler, bir listedeki ilk belge bağlamını bulmak için bir karşılaştırma ölçütü belirtmek için kullanılır. Belge bağlamına, yöntemi aracılığıyla kendisini karşılaştırmak için belge bağlamlarının bir listesi verilir `IDebugDocumentContext2::Compare` . Karşılaştırma işlecinin daha sonra döndürüldüğü listedeki ilk belge bağlamı `true` döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Karşılaştır](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)
