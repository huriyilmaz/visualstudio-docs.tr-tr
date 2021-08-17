---
description: Kesme noktası ayarlarken ek bilgi belirtmek için kullanılmaktadır isteğe bağlı bayraklar sağlar.
title: BP_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_FLAGS
helpviewer_keywords:
- BP_FLAGS enumeration
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5f0d79bd6e3c1495f85ed6f8436a781445173810
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122104657"
---
# <a name="bp_flags"></a>BP_FLAGS
Kesme noktası ayarlarken ek bilgi belirtmek için kullanılmaktadır isteğe bağlı bayraklar sağlar.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BP_FLAGS {
    BP_FLAG_NONE            = 0x0000,
    BP_FLAG_MAP_DOCPOSITION = 0x0001,
    BP_FLAG_DONT_STOP       = 0x0002
};
typedef DWORD BP_FLAGS;
```

```csharp
public enum enum_BP_FLAGS {
    BP_FLAG_NONE            = 0x0000,
    BP_FLAG_MAP_DOCPOSITION = 0x0001,
    BP_FLAG_DONT_STOP       = 0x0002
};
```

## <a name="fields"></a>Alanlar
`BP_FLAG_NONE`\
Kesme noktası bayrağı olmadığını belirtir.

`BP_FLAG_MAP_DOCPOSITION`\
Hata ayıklama altyapısının (DE) belge konumunu kullanarak kesme noktasıyla eşlemesi gerektiğini belirtir. Bu yalnızca Active Server Pages (ASP) gibi betik yönelimli kaynak dosyalarda ayarlanmış kesme noktaları için geçerlidir.

`BP_FLAG_DONT_STOP`\
Kesme noktası hata ayıklama altyapısı tarafından işlenmeli, ancak hata ayıklama altyapısının sonunda orada durmama gerektiğini belirtir (yani, [bir IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) olay nesnesi gönderilmez). Bu bayrak öncelikli olarak izleme noktalarıyla birlikte kullanılacak şekilde tasarlanmıştır.

## <a name="remarks"></a>Açıklamalar
BP_REQUEST_INFO `dwFlags` ve [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info.md) için kullanılır. [](../../../extensibility/debugger/reference/bp-request-info2.md)

Bu değerler bitwise ile birleştirilmiş `OR` olabilir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
