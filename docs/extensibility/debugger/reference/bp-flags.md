---
title: BP_FLAGS | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_FLAGS
helpviewer_keywords:
- BP_FLAGS enumeration
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 62626ff75a4545d89835d3136649191004291f8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738067"
---
# <a name="bp_flags"></a>BP_FLAGS
Kesme noktası ayarlarken ek bilgi belirtmek için kullanılabilecek isteğe bağlı bayraklar sağlar.

## <a name="syntax"></a>Sözdizimi

```cpp
enum enum_BP_FLAGS {
    BP_FLAG_NONE            = 0x0000,
    BP_FLAG_MAP_DOCPOSITION = 0x0001,
    BP_FLAG_DONT_STOP       = 0x0002
};
typedef DWORD BP_FLAGS;
```

```csharp
public enum enum_BP_FLAGS {
    BP_FLAG_NONE            = 0x0000,
    BP_FLAG_MAP_DOCPOSITION = 0x0001,
    BP_FLAG_DONT_STOP       = 0x0002
};
```

## <a name="fields"></a>Alanlar
`BP_FLAG_NONE`\
Kesme noktası bayrağı belirtin.

`BP_FLAG_MAP_DOCPOSITION`\
Hata ayıklama altyapısının (DE) belge konumunu kullanarak kesme noktasını eşlemesi gerektiğini belirtir. Bu yalnızca Active Server Pages (ASP) gibi komut dosyası yönelimli kaynak dosyalarda ayarlanan kesme noktaları için geçerlidir.

`BP_FLAG_DONT_STOP`\
Kesme noktasının hata ayıklama altyapısı tarafından işlenmesi gerektiğini, ancak hata ayıklama altyapısının nihayetinde orada durmaması gerektiğini belirtir (diğer bir şekilde bir [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) olay nesnesi gönderilmemelidir). Bu bayrak öncelikle izleme noktaları ile kullanılmak üzere tasarlanmıştır.

## <a name="remarks"></a>Açıklamalar
[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) ve `dwFlags` [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) yapıların üyesi için kullanılır.

Bu değerler biraz ile `OR`birleştirilebilir.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
