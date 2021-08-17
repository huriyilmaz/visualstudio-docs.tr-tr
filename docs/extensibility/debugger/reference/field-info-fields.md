---
description: Bir IDebugField nesnesi hakkında hangi bilgilerin alın başkanı olduğunu belirtir.
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 03b89d7337888033b2a2ce02e71d37a1340a4580
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073038"
---
# <a name="field_info_fields"></a>FIELD_INFO_FIELDS
[Bir IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesnesi hakkında hangi bilgilerin alın başkanı olduğunu belirtir.

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
Çalışma alanı `bstrFullName` yapısında alanını [FIELD_INFO.](../../../extensibility/debugger/reference/field-info.md)

`FIF_NAME`\
Yapıda alanını `bstrName` `FIELD_INFO` başlatma/kullanma.

`FIF_TYPE`\
Yapıda alanını `bstrType` `FIELD_INFO` başlatma/kullanma.

`FIF_MODIFIERS`\
Yapıda alanını `bstrModifiers` `FIELD_INFO` başlatma/kullanma.

## <a name="remarks"></a>Açıklamalar
Bu değerler ayrıca, yeni yapının hangi alanlarının başlat olacağını belirtmek için [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) bağımsız değişken olarak geçirebilirsiniz.

Bu değerler, hangi alanların `dwFields` kullandır ve `FIELD_INFO` geçerli olduğunu belirtmek için yapının üyesinde de kullanılır.

Bu bayraklar bit olarak birleştirilmiş `OR` olabilir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: sh.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
