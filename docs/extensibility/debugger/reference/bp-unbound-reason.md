---
title: BP_UNBOUND_REASON | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b0ee695e1108bf9f1c6069084a0826ee23bf37d4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737776"
---
# <a name="bp_unbound_reason"></a>BP_UNBOUND_REASON
Bir kırılma noktasının bağlanmamasının nedenini verir.

## <a name="syntax"></a>Sözdizimi

```cpp
enum enum_BP_UNBOUND_REASON {
    BPUR_UNKNOWN           = 0x0000,
    BPUR_CODE_UNLOADED     = 0x0002,
    BPUR_BREAKPOINT_REBIND = 0x0003,
    BPUR_BREAKPOINT_ERROR  = 0x0004
};
typedef DWORD BP_UNBOUND_REASON;
```

```csharp
public enum enum_BP_UNBOUND_REASON {
    BPUR_UNKNOWN           = 0x0000,
    BPUR_CODE_UNLOADED     = 0x0002,
    BPUR_BREAKPOINT_REBIND = 0x0003,
    BPUR_BREAKPOINT_ERROR  = 0x0004
};
```

## <a name="fields"></a>Alanlar
`BPUR_UNKNOWN`\
Nedeni bilinmiyor.

`BPUR_CODE_UNLOADED`\
Kesme noktasını içeren kod kaldırıldı.

`BPUR_BREAKPOINT_REBIND`\
Kırılma noktası farklı bir konuma geri tepme oldu. Bu, kesme noktası hareket ettiğinde veya kesme noktası artık geçerli olmayan bir yola sahip bir dosyaya bağlandığında, İşlemleri Edit ve Devam'tan sonra gerçekleşebilir.

`BPUR_ BREAKPOINT_ERROR`\
Kesme noktası bağlandıktan sonra hata olarak belirlenir. Bu, koşulları artık geçerli olmayan yönetilen kesme noktalarına olur.

## <a name="remarks"></a>Açıklamalar
[GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) yöntemiyle döndürülür.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)
