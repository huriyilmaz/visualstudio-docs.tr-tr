---
description: Bu yapı, bir makinede çalışan süreçler hakkında bilgi sağlar.
title: PROVIDER_PROCESS_DATA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROVIDER_PROCESS_DATA
helpviewer_keywords:
- PROVIDER_PROCESS_DATA structure
ms.assetid: ec2362ed-4a0c-4a09-9d66-8ff04e4f41ee
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a6c48c87f92fde487b9a008c5db45f75eb026f83
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079520"
---
# <a name="provider_process_data"></a>PROVIDER_PROCESS_DATA
Bu yapı, bir makinede çalışan süreçler hakkında bilgi sağlar.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagPROVIDER_PROCESS_DATA {
   PROVIDER_FIELDS    Fields;
   PROGRAM_NODE_ARRAY ProgramNodes;
   BOOL               fIsDebuggerPresent;
} PROVIDER_PROCESS_DATA;
```

```csharp
public struct PROVIDER_PROCESS_DATA {
   public uint               Fields;
   public PROGRAM_NODE_ARRAY ProgramNodes;
   public int                fIsDebuggerPresent;
}
```

## <a name="members"></a>Üyeler
 `Fields`\
 [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md) numaralandırmasından, hangi alanların doldurulacağını belirten bayrakların birleşimi.

 `ProgramNodes`\
 Program düğümleri dizisini içeren [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) yapısı.

 `fIsDebuggerPresent`\
 `TRUE` [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Hata ayıklayıcı çalışıyorsa sıfır olmayan () sıfır ( `FALSE` ).

## <a name="remarks"></a>Açıklamalar
 Bu yapı, doldurulduğu [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) yöntemine geçirilir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)
- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
