---
title: BP_FLAGS90 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5628af4a6e5c4deae3de02340e882bd2605e22d3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738053"
---
# <a name="bp_flags90"></a>BP_FLAGS90
İsteğe bağlı bayraklar için geçerli değerleri oyalar. Bir kesme noktası ayarladığınızda isteğe bağlı bayraklar ek bilgi belirtmek için kullanılabilir. Bu numaralandırma [numaralandırma BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) genişletir.

## <a name="syntax"></a>Sözdizimi

```cpp
enum enum_BP_FLAGS90
{
    // VS 8.0 values
    BP90_FLAG_NONE               = 0x0000,
    BP90_FLAG_MAP_DOCPOSITION    = 0x0001,
    BP90_FLAG_DONT_STOP          = 0x0002,

    // Values added in VS 9.0
    BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,
};
typedef DWORD BP_FLAGS90;
```

```csharp
public enum enum_BP_FLAGS90
{
    // VS 8.0 values
    BP90_FLAG_NONE                = 0x0000,
    BP90_FLAG_MAP_DOCPOSITION     = 0x0001,
    BP90_FLAG_DONT_STOP           = 0x0002,

    // Values added in VS 9.0
    BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,
};
```

## <a name="fields"></a>Alanlar
`BP90_FLAG_NONE`\
Kesme noktası bayrağı belirtin.

`BP90_FLAG_MAP_DOCPOSITION`\
Hata ayıklama altyapısının (DE) belge konumunu kullanarak kesme noktasını eşlemesi gerektiğini belirtir. Bu yalnızca Active Server Pages (ASP) gibi komut dosyası yönelimli kaynak dosyalarda ayarlanan kesme noktaları için geçerlidir.

`BP90_FLAG_DONT_STOP`\
Kesme noktasının hata ayıklama motoru tarafından işlenmesi gerektiğini, ancak hata ayıklama altyapısının nihayetinde burada durmaması gerektiğini belirtir; diğer bir de, bir [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) olay nesnesi gönderilmemelidir. Bu bayrak öncelikle izleme noktaları ile kullanılmak üzere tasarlanmıştır.

`BP90_FLAG_TRACEPOINT_CONTINUE`\
Atlama durumunun temizlenip temizlenmemesi gerektiğini belirlemek için yerel hata ayıklama altyapısı tarafından kullanılır. İzleme noktası bir makro yürütürse BP90_FLAG_DONT_STOP ayarlanmadığından, BP90_FLAG_DONT_STOP farklıdır.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: Msdbg90.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
