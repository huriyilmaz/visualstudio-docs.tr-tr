---
description: Bu yapı yerel bir değişkeni, parametreyi veya başka bir alanı açıklar.
title: FIELD_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO
helpviewer_keywords:
- FIELD_INFO structure
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2a0d549ef0327b9894e50a7d849be4b6688df83c8e903e14778b3827f7e82f2d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121360800"
---
# <a name="field_info"></a>FIELD_INFO
Bu yapı yerel bir değişkeni, parametreyi veya başka bir alanı açıklar.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagFieldInfo {
    FIELD_INFO_FIELDS dwFields;
    BSTR              bstrFullName;
    BSTR              bstrName;
    BSTR              bstrType;
    FIELD_MODIFIERS   dwModifiers;
} FIELD_INFO;
```

```csharp
public struct FIELD_INFO {
    public uint   dwFields;
    public string bstrFullName;
    public string bstrName;
    public string bstrType;
    public uint   dwModifiers;
};
```

## <a name="members"></a>Üyeler
`dwFields`\
Hangi üyelerin [doldurulması FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) bir bayrak birleşimi.

`bstrFullName`\
Alanın tam adı.

`bstrName`\
Alanın kısa adı.

`bstrType`\
Alanın türü.

`dwModifiers`\
Alanı açıklayan bir [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) bayrağı birleşimi.

## <a name="remarks"></a>Açıklamalar
Bu yapı, [doldurulan GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) yöntemine geçirildi.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: sh.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
