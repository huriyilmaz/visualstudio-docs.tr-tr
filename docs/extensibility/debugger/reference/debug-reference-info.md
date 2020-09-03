---
title: DEBUG_REFERENCE_INFO | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737406"
---
# <a name="debug_reference_info"></a>DEBUG_REFERENCE_INFO
Bir başvuruyu açıklar.

## <a name="syntax"></a>Syntax

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
[DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) Numaralandırmadaki, doldurulacak alanları belirten bayrakların birleşimi.

`bstrName`\
[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) nesnesinin kullanıcı tarafından belirtilen adı.

`bstrType`\
Bir biçimli dize olarak başvuru türü.

`bstrValue`\
Bir biçimli dize olarak başvuru değeri

`dwAttrib`\
Hata ayıklama özelliği özniteliklerinin bayraklarını belirten [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) numaralandırmasındaki bayrakların birleşimi.

`dwRefType`\
[REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) numaralandırmasından, başvuru türünün güçlü veya zayıf olduğunu belirten bir değer.

`m_pReference`\
Başvuru bilgilerini belirten bir [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) nesnesi.

## <a name="remarks"></a>Açıklamalar
Bu yapı, doldurulacak [Getreferenceınfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) metoduna yapılan çağrıya geçirilir. Bu yapı Ayrıca, [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) arabiriminden bir listenin parçası olarak da döndürülür, bu da [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) yöntemine yapılan çağrıdan döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
