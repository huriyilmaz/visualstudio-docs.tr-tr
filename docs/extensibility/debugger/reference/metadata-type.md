---
description: METADATA_TYPE yapısı, meta verilerden alınan bir alan türü hakkında bilgi belirtir.
title: METADATA_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a76e051e146985338564d497323b6232b35a4a1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079858"
---
# <a name="metadata_type"></a>METADATA_TYPE
Bu yapı, meta verilerden alınan bir alan türü hakkında bilgi belirtir.

## <a name="syntax"></a>Sözdizimi

```cpp
typedef struct _tagTYPE_METADATA {
   ULONG32  ulAppDomainID;
   GUID     guidModule;
   _mdToken tokClass;
} METADATA_TYPE;
```

```csharp
public struct METADATA_TYPE {
   public uint ulAppDomainID;
   public Guid guidModule;
   public int  tokClass;
};
```

## <a name="parameters"></a>Parametreler
 `ulAppDomainID`\
 Simgenin geldiği uygulamanın KIMLIĞI. Bu, uygulamanın bir örneğini benzersiz bir şekilde tanımlamak için kullanılır.

 `guidModule`\
 Bu alanı içeren modülün GUID 'ı.

 `tokClass`\
 Bu türün meta veri belirteci KIMLIĞI.

 [C++] `_mdToken` , `typedef` 32 bitlik bir içindir `int` .

## <a name="remarks"></a>Açıklamalar
 Bu yapı, [](../../../extensibility/debugger/reference/type-info.md) `dwKind` `TYPE_INFO` yapı alanı `TYPE_KIND_METADATA` ( [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) numaralandırmasından bir değer) olarak ayarlandığında TYPE_INFO yapısındaki birleşimin bir parçası olarak görüntülenir.

 `tokClass`Değer, bir türü benzersiz bir şekilde tanımlayan bir meta veri belirtecidir. Meta veri belirteci KIMLIĞININ üst bitlerini yorumlama hakkında daha fazla bilgi için `CorTokenType` .NET Framework SDK 'sindeki CorHdr. h dosyasındaki sabit listesine bakın.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: SH. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
