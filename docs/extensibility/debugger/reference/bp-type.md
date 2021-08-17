---
description: Kesme noktası bir kod konumu, veri konumu veya başka bir kesme noktası türü olup olmadığını belirtir.
title: BP_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_TYPE
helpviewer_keywords:
- BP_TYPE enumeration
ms.assetid: ef07191e-7966-43ab-96fb-1a0b1db3115d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 87680df78d4b7ba733f55b5070b1d89f5f2a2d07b664d2f1f38a92848d3a65b5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121390462"
---
# <a name="bp_type"></a>BP_TYPE
Kesme noktası bir kod konumu, veri konumu veya başka bir kesme noktası türü olup olmadığını belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BP_TYPE {
    BPT_NONE    = 0x0000,
    BPT_CODE    = 0x0001,
    BPT_DATA    = 0x0002,
    BPT_SPECIAL = 0x0003
};
typedef DWORD BP_TYPE;
```

```csharp
public enum enum_BP_TYPE {
    BPT_NONE    = 0x0000,
    BPT_CODE    = 0x0001,
    BPT_DATA    = 0x0002,
    BPT_SPECIAL = 0x0003
};
```

## <a name="fields"></a>Alanlar
`BPT_NONE`\
Kesme noktası türünü belirtir.

`BPT_CODE`\
Bir kod kesme noktası belirtir.

`BPT_DATA`\
Bir veri kesme noktası belirtir.

`BPT_SPECIAL`\
Kod veya veri türü olan bir kesme noktası belirtir. Bu tür kullanım dışıdır ve kullanılmamalı.

## <a name="remarks"></a>Açıklamalar
[GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md) ve [GetBreakpointType yöntemlerine parametre olarak](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md) geçirildi.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)
- [GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)
