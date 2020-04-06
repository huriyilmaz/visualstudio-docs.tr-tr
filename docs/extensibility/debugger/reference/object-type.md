---
title: OBJECT_TYPE | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- OBJECT_TYPE
helpviewer_keywords:
- OBJECT_TYPE enumeration
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4ffb85a14e42dd57c345481285eb1f776b3866d3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714125"
---
# <a name="object_type"></a>OBJECT_TYPE
İfade değerlendiricisinden bir nesnenin türünü belirtir.

## <a name="syntax"></a>Sözdizimi

```cpp
enum enum_OBJECT_TYPE { 
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
public enum enum_OBJECT_TYPE { 
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
 Nesnenin Boolean olduğunu gösterir.

 `OBJECT_TYPE_CHAR`\
 Nesnenin bir karakter olduğunu gösterir.

 `OBJECT_TYPE_I1`\
 Nesnenin tek bayt imzalı bir tamsayı olduğunu gösterir.

 `OBJECT_TYPE_U1`\
 Nesnenin bir bayt imzasız tamsayı olduğunu gösterir.

 `OBJECT_TYPE_I2`\
 Nesnenin iki bayt imzalı bir tamsayı olduğunu gösterir.

 `OBJECT_TYPE_U2`\
 Nesnenin iki bayt imzasız bir tamsayı olduğunu gösterir.

 `OBJECT_TYPE_I4`\
 Nesnenin dört bayt imzalı bir tamsayı olduğunu gösterir.

 `OBJECT_TYPE_U4`\
 Nesnenin dört bayt imzasız bir tamsayı olduğunu gösterir.

 `OBJECT_TYPE_I8`\
 Nesnenin sekiz bayt imzalı bir karşımat olduğunu gösterir.

 `OBJECT_TYPE_U8`\
 Nesnenin sekiz bayt imzasız bir karşıcı olduğunu gösterir.

 `OBJECT_TYPE_R4`\
 Nesnenin dört bayt kayan nokta numarası olduğunu gösterir.

 `OBJECT_TYPE_R8`\
 Nesnenin sekiz bayt kayan nokta lı bir sayı olduğunu gösterir.

 `OBJECT_TYPE_OBJECT`\
 Nesnenin bir nesne olduğunu gösterir.

 `OBJECT_TYPE_NULL`\
 Nesnenin NULL olduğunu gösterir.

 `OBJECT_TYPE_CLASS`\
 Nesnenin bir sınıf olduğunu gösterir.

## <a name="remarks"></a>Açıklamalar
 [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md) ve [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md) yöntemlerine bağımsız değişken olarak geçirilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: ee.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)
- [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)
