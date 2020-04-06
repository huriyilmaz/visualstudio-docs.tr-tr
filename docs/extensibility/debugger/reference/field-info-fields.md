---
title: FIELD_INFO_FIELDS | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9a3d2e796d37606c51918d8e49db920161d63f55
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736902"
---
# <a name="field_info_fields"></a>FIELD_INFO_FIELDS
Bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesnesi hakkında hangi bilgilerin alıncaya kadar alınacağa ilişkindir.

## <a name="syntax"></a>Sözdizimi

```cpp
enum enum_FIELD_INFO_FIELDS { 
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
`bstrFullName` [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) yapısındaki alanı başlatma/kullanma.

`FIF_NAME`\
`FIELD_INFO` Yapıdaki `bstrName` alanı başlatma/kullanma.

`FIF_TYPE`\
`FIELD_INFO` Yapıdaki `bstrType` alanı başlatma/kullanma.

`FIF_MODIFIERS`\
`FIELD_INFO` Yapıdaki `bstrModifiers` alanı başlatma/kullanma.

## <a name="remarks"></a>Açıklamalar
Bu değerler, [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) yapının hangi alanlarının başharfe atılolacağını belirtmek için [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) yöntemine bir bağımsız değişken olarak da geçirilir.

Bu değerler, `dwFields` `FIELD_INFO` yapının üyesinde hangi alanların kullanıldığını ve geçerli olduğunu belirtmek için de kullanılır.

Bu bayraklar biraz ile `OR`birleştirilebilir.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: sh.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
