---
title: DEBUG_REFERENCE_INFO | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REFERENCE_INFO
helpviewer_keywords:
- DEBUG_REFERENCE_INFO structure
ms.assetid: 24b83d00-d756-42a1-8083-730f998761dc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6e31205f52151679f932877c9c4fdc56907ea59e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737406"
---
# <a name="debug_reference_info"></a>DEBUG_REFERENCE_INFO
Bir başvuru açıklar.

## <a name="syntax"></a>Sözdizimi

```cpp
typedef struct tagDEBUG_REFERENCE_INFO {
    DEBUGREF_INFO_FLAGS dwFields;
    BSTR                bstrName;
    BSTR                bstrType;
    BSTR                bstrValue;
    DBG_ATTRIB_FLAGS    dwAttrib;
    REFERENCE_TYPE.     dwRefType;
    IDebugReference2*   m_pReference;
} DEBUG_REFERENCE_INFO;
```

```csharp
public struct DEBUG_REFERENCE_INFO {
    public uint             dwFields;
    public string           bstrName;
    public string           bstrType;
    public string           bstrValue;
    public ulong            dwAttrib;
    public uint.            dwRefType;
    public IDebugReference2 m_pReference;
};
```

## <a name="members"></a>Üyeler
`dwFields`\
Hangi alanların [doldurulduğuna](../../../extensibility/debugger/reference/debugref-info-flags.md) DEBUGREF_INFO_FLAGS numaralandırmadaki bayrakların birleşimi.

`bstrName`\
[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) nesnesinin kullanıcı tarafından belirtilen adı.

`bstrType`\
Biçimlendirilmiş dize olarak başvuru türü.

`bstrValue`\
Biçimlendirilmiş dize olarak başvuru değeri

`dwAttrib`\
Hata ayıklama özelliği öznitelikleri için bayrakları belirten [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) numaralandırma bayraklarının birleşimi.

`dwRefType`\
Başvuru türünün güçlü veya zayıf olup olmadığını belirten [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) numaralandırma değeri.

`m_pReference`\
Başvuru bilgilerini belirten bir [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) nesnesi.

## <a name="remarks"></a>Açıklamalar
Bu yapı doldurulmak üzere [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) yöntemine bir çağrıya geçirilir. Bu yapı aynı zamanda, sırayla, [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) yöntemine bir çağrı döndürülür [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) arabiriminden bir listenin bir parçası olarak döndürülür.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
