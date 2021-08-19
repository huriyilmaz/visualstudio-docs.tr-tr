---
description: Bir IDebugField nesnesinin içerebileceği ek alan türlerini numaralandırır.
title: FIELD_KIND_EX | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- FIELD_KIND_EX enumeration
ms.assetid: 922c3208-1e94-485f-b70a-3bc96affeff8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0fa15be35ff92cbee20ce279da80faf7e7e588a2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122072908"
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
