---
title: OBJECT_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- OBJECT_TYPE
helpviewer_keywords:
- OBJECT_TYPE enumeration
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad51e8db72cba874d35f66c9759fb970ffff2716
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911708"
---
# <a name="object_type"></a>OBJECT_TYPE
İfade değerlendirici ' nden bir nesne türünü belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_OBJECT_TYPE { 
   OBJECT_TYPE_BOOLEAN = 0x0,
   OBJECT_TYPE_CHAR    = 0x1,
   OBJECT_TYPE_I1      = 0x2,
   OBJECT_TYPE_U1      = 0x3,
   OBJECT_TYPE_I2      = 0x4,
   OBJECT_TYPE_U2      = 0x5,
   OBJECT_TYPE_I4      = 0x6,
   OBJECT_TYPE_U4      = 0x7,
   OBJECT_TYPE_I8      = 0x8,
   OBJECT_TYPE_U8      = 0x9,
   OBJECT_TYPE_R4      = 0xa,
   OBJECT_TYPE_R8      = 0xb,
   OBJECT_TYPE_OBJECT  = 0xc,
   OBJECT_TYPE_NULL    = 0xd,
   OBJECT_TYPE_CLASS   = 0xe
};
typedef DWORD OBJECT_TYPE;
```

```csharp
public enum enum_OBJECT_TYPE { 
   OBJECT_TYPE_BOOLEAN = 0x0,
   OBJECT_TYPE_CHAR    = 0x1,
   OBJECT_TYPE_I1      = 0x2,
   OBJECT_TYPE_U1      = 0x3,
   OBJECT_TYPE_I2      = 0x4,
   OBJECT_TYPE_U2      = 0x5,
   OBJECT_TYPE_I4      = 0x6,
   OBJECT_TYPE_U4      = 0x7,
   OBJECT_TYPE_I8      = 0x8,
   OBJECT_TYPE_U8      = 0x9,
   OBJECT_TYPE_R4      = 0xa,
   OBJECT_TYPE_R8      = 0xb,
   OBJECT_TYPE_OBJECT  = 0xc,
   OBJECT_TYPE_NULL    = 0xd,
   OBJECT_TYPE_CLASS   = 0xe
};
```

## <a name="fields"></a>Alanlar
 `OBJECT_TYPE_BOOLEAN`\
 Nesnenin Boole olduğunu gösterir.

 `OBJECT_TYPE_CHAR`\
 Nesnenin bir karakter olduğunu gösterir.

 `OBJECT_TYPE_I1`\
 Nesnenin tek baytlık işaretli bir tamsayı olduğunu gösterir.

 `OBJECT_TYPE_U1`\
 Nesnenin tek baytlık işaretsiz bir tamsayı olduğunu gösterir.

 `OBJECT_TYPE_I2`\
 Nesnenin iki baytlık işaretli bir tamsayı olduğunu gösterir.

 `OBJECT_TYPE_U2`\
 Nesnenin iki baytlık işaretsiz bir tamsayı olduğunu gösterir.

 `OBJECT_TYPE_I4`\
 Nesnenin dört baytlık işaretli bir tamsayı olduğunu gösterir.

 `OBJECT_TYPE_U4`\
 Nesnenin dört baytlık işaretsiz bir tamsayı olduğunu gösterir.

 `OBJECT_TYPE_I8`\
 Nesnenin sekiz baytlık işaretli bir tamsayı olduğunu gösterir.

 `OBJECT_TYPE_U8`\
 Nesnenin sekiz baytlık işaretsiz bir tamsayı olduğunu gösterir.

 `OBJECT_TYPE_R4`\
 Nesnenin dört baytlık kayan noktalı sayı olduğunu gösterir.

 `OBJECT_TYPE_R8`\
 Nesnenin sekiz baytlık kayan noktalı sayı olduğunu gösterir.

 `OBJECT_TYPE_OBJECT`\
 Nesnenin bir nesne olduğunu gösterir.

 `OBJECT_TYPE_NULL`\
 Nesnenin NULL olduğunu gösterir.

 `OBJECT_TYPE_CLASS`\
 Nesnenin bir sınıf olduğunu belirtir.

## <a name="remarks"></a>Açıklamalar
 [Createprimitiveobject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md) ve [createarrayobject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md) yöntemlerine bir bağımsız değişken olarak geçirilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: ee. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)
- [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)
