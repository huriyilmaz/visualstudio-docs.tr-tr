---
description: Bir hata ayıklama başvuru nesnesi hakkında hangi bilgilerin yapılacağını belirtir.
title: DEBUGREF_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGREF_INFO_FLAGS
helpviewer_keywords:
- DEBUGREF_INFO_FLAGS enumeration
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a9a765ec2f4c8b2f6bc2366465938d5bd8dd1614
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122111716"
---
# <a name="debugref_info_flags"></a>DEBUGREF_INFO_FLAGS
Bir hata ayıklama başvuru nesnesi hakkında hangi bilgilerin yapılacağını belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_DEBUGREF_INFO_FLAGS {
    DEBUGREF_INFO_NAME             = 0x00000001,
    DEBUGREF_INFO_TYPE             = 0x00000002,
    DEBUGREF_INFO_VALUE            = 0x00000004,
    DEBUGREF_INFO_ATTRIB           = 0x00000008,
    DEBUGREF_INFO_REFTYPE          = 0x00000010,
    DEBUGREF_INFO_REF              = 0x00000020,
    DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,
    DEBUGREF_INFO_NONE             = 0x00000000,
    DEBUGREF_INFO_ALL              = 0xffffffff
};
typedef DWORD DEBUGREF_INFO_FLAGS;
```

```csharp
public enum enum_DEBUGREF_INFO_FLAGS {
    DEBUGREF_INFO_NAME             = 0x00000001,
    DEBUGREF_INFO_TYPE             = 0x00000002,
    DEBUGREF_INFO_VALUE            = 0x00000004,
    DEBUGREF_INFO_ATTRIB           = 0x00000008,
    DEBUGREF_INFO_REFTYPE          = 0x00000010,
    DEBUGREF_INFO_REF              = 0x00000020,
    DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,
    DEBUGREF_INFO_NONE             = 0x00000000,
    DEBUGREF_INFO_ALL              = 0xffffffff
};
```

## <a name="fields"></a>Alanlar
`DEBUGREF_INFO_NAME`\
Yapıda alanı başlatın/kullanın `bstrName` .

`DEBUGREF_INFO_TYPE`\
Yapıda alanı başlatın/kullanın `bstrType` .

`DEBUGREF_INFO_VALUE`\
Yapıda alanı başlatın/kullanın `bstrValue` .

`DEBUGREF_INFO_ATTRIB`\
Yapıda alanı başlatın/kullanın `dwAttrib` .

`DEBUGREF_INFO_REFTYPE`\
Yapıda alanı başlatın/kullanın `dwRefType` .

`DEBUGREF_INFO_REF`\
Yapıda alanı başlatın/kullanın `pReference` .

`DEBUGREF_INFO_VALUE_AUTOEXPAND`\
Değer alanı, varsa, bu nesne türü için otomatik genişletilmiş değeri içermelidir.

`DEBUGREF_INFO_NONE`\
Hiçbir bayrak belirlenmediğini gösterir.

`DEBUGREF_INFO_ALL`\
Bayrakların maskesini belirtir.

## <a name="remarks"></a>Açıklamalar
Bu bayraklar, [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) yapısının hangi alanlarının başlatıldığını göstermek Için [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) ve [getreferenceınfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) yöntemlerine geçirilir.

Yapı öğesi için, `dwFields` `DEBUG_REFERENCE_INFO` Yapı döndürüldüğünde hangi alanların kullanıldığını ve geçerli olduğunu göstermek için kullanılır.

Bu değerler, bit düzeyinde birleştirilebilir `OR` .

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
