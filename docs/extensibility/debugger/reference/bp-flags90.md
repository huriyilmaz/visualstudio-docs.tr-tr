---
title: BP_FLAGS90 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 95992d32df6b05c182b5b0ca505bc288294e282c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923230"
---
# <a name="bp_flags90"></a>BP_FLAGS90
İsteğe bağlı bayraklar için geçerli değerleri numaralandırır. İsteğe bağlı bayraklar, bir kesme noktası ayarladığınızda ek bilgi belirtmek için kullanılabilir. Bu sabit listesi [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) numaralandırmayı genişletir.

## <a name="syntax"></a>Syntax

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
Kesme noktası bayrağı olmadığını belirtir.

`BP90_FLAG_MAP_DOCPOSITION`\
Hata ayıklama altyapısının (DE), belge konumunu kullanarak kesme noktasını eşlemesi gerektiğini belirtir. Bu yalnızca, Active Server sayfaları (ASP) gibi komut dosyası yönelimli kaynak dosyalarında ayarlanan kesme noktaları için geçerlidir.

`BP90_FLAG_DONT_STOP`\
Kesme noktasının hata ayıklama altyapısı tarafından işlenmesi gerektiğini, ancak hata ayıklama altyapısının sonunda bu şekilde durdurulmadığını belirtir; diğer bir deyişle, bir [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) olay nesnesi gönderilmemelidir. Bu bayrak, birincil olarak izleme noktalarıyla kullanılmak üzere tasarlanmıştır.

`BP90_FLAG_TRACEPOINT_CONTINUE`\
Yerel hata ayıklama altyapısı tarafından, Adımlama durumunun temizlenip temizlenmeyeceğini tespit etmek için kullanılır. İzleme noktası bir makro yürüttüğünde BP90_FLAG_DONT_STOP ayarlanmadığından BP90_FLAG_DONT_STOP farklıdır.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: Msdbg90. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
