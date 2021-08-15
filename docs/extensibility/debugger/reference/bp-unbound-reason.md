---
description: Bir kesme noktasıyla bağlantının kopma nedenini verir.
title: BP_UNBOUND_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ddf18bf8a9ce0e31e3ff692f202b9c274854f10ad7f69c0bc4b5edffc92c1fb4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121239314"
---
# <a name="bp_unbound_reason"></a>BP_UNBOUND_REASON
Bir kesme noktasıyla bağlantının kopma nedenini verir.

## <a name="syntax"></a>Syntax

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
Kesme noktası içeren kod kaldırıldı.

`BPUR_BREAKPOINT_REBIND`\
Kesme noktası farklı bir konuma geri geldi. Kesme noktası hareket ettiğinde veya kesme noktası artık geçerli olmayan bir yola sahip bir dosyaya bağlı olduğunda, Düzenle ve Devam Edin işlemleri sonrasında bu durum olabilir.

`BPUR_ BREAKPOINT_ERROR`\
Kesme noktası bağlandıktan sonra hatada olduğu belirlenir. Bu, koşulları artık geçerli olmayan yönetilen kesme noktalarına gerçekleşir.

## <a name="remarks"></a>Açıklamalar
[GetReason yöntemi tarafından](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)
