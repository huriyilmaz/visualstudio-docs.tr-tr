---
title: FIELD_KIND_EX | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- FIELD_KIND_EX enumeration
ms.assetid: 922c3208-1e94-485f-b70a-3bc96affeff8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d3742e60c1bc8a0e490ca83ba14eadc4b879d3e1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936905"
---
# <a name="field_kind_ex"></a>FIELD_KIND_EX
Bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesnesinin içerebileceği ek alan türlerini numaralandırır. Bu sabit listesi [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) numaralandırmayı genişletir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_FIELD_KIND_EX
{
    FIELD_KIND_EX_NONE = 0,
    FIELD_TYPE_EX_METHODVAR = 0x1,
    FIELD_TYPE_EX_CLASSVAR = 0x2
};
typedef DWORD FIELD_KIND_EX;
```

```csharp
public enum enum_FIELD_KIND_EX
{
    FIELD_KIND_EX_NONE = 0,
    FIELD_TYPE_EX_METHODVAR = 0x1,
    FIELD_TYPE_EX_CLASSVAR = 0x2
};
```

## <a name="fields"></a>Alanlar
`FIELD_KIND_EX_NONE`\
Alan, genişletilmiş bir tür içermiyor.

`FIELD_TYPE_EX_METHODVAR`\
Alan bir yöntem değişkeni içeriyor.

`FIELD_TYPE_EX_CLASSVAR`\
Alan bir sınıf değişkeni içeriyor.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: SH. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)
