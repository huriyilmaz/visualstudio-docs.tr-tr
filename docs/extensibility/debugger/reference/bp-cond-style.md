---
description: Bekleyen ve bağlı kesme noktaları için kesme noktası koşul stilini belirtir.
title: BP_COND_STYLE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 66be01a2a6de30aa0a4b8d59cb0e3575890d0a8a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122104683"
---
# <a name="bp_cond_style"></a>BP_COND_STYLE
Bekleyen ve bağlı kesme noktaları için kesme noktası koşul stilini belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BP_COND_STYLE {
    BP_COND_NONE         = 0x0000,
    BP_COND_WHEN_TRUE    = 0x0001,
    BP_COND_WHEN_CHANGED = 0x0002
};
typedef DWORD BP_COND_STYLE;
```

```csharp
public enum enum_BP_COND_STYLE {
    BP_COND_NONE         = 0x0000,
    BP_COND_WHEN_TRUE    = 0x0001,
    BP_COND_WHEN_CHANGED = 0x0002
};
```

## <a name="fields"></a>Alanlar
`BP_COND_NONE`\
Kesme noktası konumuna ulaşıldıklarda kesme noktası tarafından 2. Kesme noktası koşulu belirtilmedi.

`BP_COND_WHEN_TRUE`\
Kesme noktası yalnızca kesme noktasıyla ilişkilendirilmiş koşullu ifade olarak değerlendir olduğunda bunu `true` sağlar.

`BP_COND_WHEN_CHANGED`\
Kesme noktası yalnızca kesme noktasıyla ilişkili koşullu ifadenin değeri önceki değerlendirmeden değiştiklerinde bu kesme noktası tarafından 2.

## <a name="remarks"></a>Açıklamalar
Bu `styleCondition` yapının üyesi [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) kullanılır.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
