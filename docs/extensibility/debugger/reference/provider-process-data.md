---
title: PROVIDER_PROCESS_DATA | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROVIDER_PROCESS_DATA
helpviewer_keywords:
- PROVIDER_PROCESS_DATA structure
ms.assetid: ec2362ed-4a0c-4a09-9d66-8ff04e4f41ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bdaf15d09af3199d026155cf7667f063f5bbe858
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713775"
---
# <a name="provider_process_data"></a>PROVIDER_PROCESS_DATA
Bu yapı, bir makinede çalışan işlemler hakkında bilgi sağlar.

## <a name="syntax"></a>Sözdizimi

```cpp
typedef struct tagPROVIDER_PROCESS_DATA {
   PROVIDER_FIELDS    Fields;
   PROGRAM_NODE_ARRAY ProgramNodes;
   BOOL               fIsDebuggerPresent;
} PROVIDER_PROCESS_DATA;
```

```csharp
public struct PROVIDER_PROCESS_DATA {
   public uint               Fields;
   public PROGRAM_NODE_ARRAY ProgramNodes;
   public int                fIsDebuggerPresent;
}
```

## <a name="members"></a>Üyeler
 `Fields`\
 [numaralandırmaPROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md) hangi alanların doldurulduğuna dair bayrakların birleşimi.

 `ProgramNodes`\
 Program düğümleri dizisi içeren [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) bir yapı.

 `fIsDebuggerPresent`\
 Nonzero`TRUE`( ) [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] hata ayıklama çalışıyorsa, sıfır (`FALSE`) değilse.

## <a name="remarks"></a>Açıklamalar
 Bu yapı, doldurulduğu [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) yöntemine geçirilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)
- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
