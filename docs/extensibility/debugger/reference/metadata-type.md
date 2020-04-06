---
title: METADATA_TYPE | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: afe5ea128775c7be0e48035ab4c7e7d370c9d233
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714297"
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
 Sembolün geldiği uygulamanın kimliği. Bu, uygulamanın bir örneğini benzersiz olarak tanımlamak için kullanılır.

 `guidModule`\
 Bu alanı içeren modülün GUID'i.

 `tokClass`\
 Bu tür meta veri belirteç kimliği.

 [C++] `_mdToken` 32-bit `typedef` `int`için bir .

## <a name="remarks"></a>Açıklamalar
 Bu yapı, `dwKind` `TYPE_INFO` yapıalanı ayarlandığında `TYPE_KIND_METADATA` [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) yapısında birliğin bir parçası olarak görünür [(dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) numaralandırmadan bir değer).

 Değer, `tokClass` bir türü benzersiz olarak tanımlayan bir meta veri belirtecidir. Meta veri belirteç kimliğinin üst bitlerinin nasıl yorumlanacağı `CorTokenType` na ilişkin ayrıntılar için ,.NET Framework SDK'daki corhdr.h dosyasındaki numaralandırmaya bakın.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: sh.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
