---
title: BP_COND_STYLE | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca704ca186308ea9e44c4fa7edc6617cbac806eb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738118"
---
# <a name="bp_cond_style"></a>BP_COND_STYLE
Bekleyen ve bağlı kesme noktaları için kesme noktası koşul stilini belirtir.

## <a name="syntax"></a>Sözdizimi

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
Kesme noktasının konumuna ulaşıldığında kesme noktasını yakalır. Kesme noktası koşulu belirtilmedi.

`BP_COND_WHEN_TRUE`\
Kesme noktası, yalnızca kesme noktasıyla ilişkili koşullu ifade `true`yi değerlendirdiğinde kesme noktasını yaslar.

`BP_COND_WHEN_CHANGED`\
Kesme noktasını yalnızca kesme noktasıyla ilişkili koşullu ifadenin değeri önceki değerlendirmesinden değiştirdiğinde yatir.

## <a name="remarks"></a>Açıklamalar
`styleCondition` [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) yapının üyesi için kullanılır.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
