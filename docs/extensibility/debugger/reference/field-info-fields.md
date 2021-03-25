---
description: Bir IDebugField nesnesi hakkında hangi bilgilerin alınması gerektiğini belirtir.
title: FIELD_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0bd13473be5817e821f61b646bd1634cfe06388b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059437"
---
# <a name="field_info_fields"></a>FIELD_INFO_FIELDS
Bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesnesi hakkında hangi bilgilerin alınması gerektiğini belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_FIELD_INFO_FIELDS { 
    FIF_FULLNAME  = 0x0001,
    FIF_NAME      = 0x0002,
    FIF_TYPE      = 0x0004,
    FIF_MODIFIERS = 0x0008,
    FIF_ALL       = 0xffffffff,
    FIF_NONE      = 0x0000
};
typedef DWORD FIELD_INFO_FIELDS;
```

```csharp
public enum enum_FIELD_INFO_FIELDS {
    FIF_FULLNAME  = 0x0001,
    FIF_NAME      = 0x0002,
    FIF_TYPE      = 0x0004,
    FIF_MODIFIERS = 0x0008,
    FIF_ALL       = 0xffffffff,
    FIF_NONE      = 0x0000
};
```

## <a name="fields"></a>Alanlar
`FIF_FULLNAME`\
`bstrFullName` [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) yapısındaki alanı başlatın/kullanın.

`FIF_NAME`\
Yapıda alanı başlatın/kullanın `bstrName` `FIELD_INFO` .

`FIF_TYPE`\
Yapıda alanı başlatın/kullanın `bstrType` `FIELD_INFO` .

`FIF_MODIFIERS`\
Yapıda alanı başlatın/kullanın `bstrModifiers` `FIELD_INFO` .

## <a name="remarks"></a>Açıklamalar
Bu değerler aynı zamanda [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) yöntemine bir bağımsız değişken olarak geçirilir ve bu da [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) yapısının hangi alanlarının başlatıldığını belirtir.

Bu değerler, `dwFields` `FIELD_INFO` hangi alanların kullanıldığını ve geçerli olduğunu göstermek için yapının üyesinde de kullanılır.

Bu bayraklar bit düzeyinde birleştirilebilir `OR` .

## <a name="requirements"></a>Gereksinimler
Üstbilgi: SH. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
