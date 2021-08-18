---
description: Bir bağlı kesme noktası varlığını belirtir ve ayrıca etkin olup o değil belirtir.
title: BP_STATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_STATE
helpviewer_keywords:
- BP_STATE enumeration
ms.assetid: 08aa6a3f-3e5f-4c83-8eca-7b7b5f8e208d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6d4136444a1d48a5ba70a9ed138897a008bbc036
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122120263"
---
# <a name="bp_state"></a>BP_STATE
Bir bağlı kesme noktası varlığını belirtir ve ayrıca etkin olup o değil belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BP_STATE {
    BPS_NONE     = 0x0000,
    BPS_DELETED  = 0x0001,
    BPS_DISABLED = 0x0002,
    BPS_ENABLED  = 0x0003
};
typedef DWORD BP_STATE;
```

```csharp
public enum enum_BP_STATE {
    BPS_NONE     = 0x0000,
    BPS_DELETED  = 0x0001,
    BPS_DISABLED = 0x0002,
    BPS_ENABLED  = 0x0003
};
```

## <a name="fields"></a>Alanlar
`BPS_NONE`\
Hiçbir kesme noktası olmadığını belirtir.

`BPS_DELETED`\
Kesme noktası silindi belirtir.

`BPS_DISABLED`\
Kesme noktası devre dışı bırakılmıştır belirtir.

`BPS_ENABLED`\
Kesme noktası etkin olduğunu belirtir.

## <a name="remarks"></a>Açıklamalar
[GetState yönteminden](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md) döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)
