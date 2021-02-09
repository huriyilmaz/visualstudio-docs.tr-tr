---
title: GUID_ARRAY | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GUID_ARRAY structure
ms.assetid: 9e12500c-2c1c-49b1-a0ba-e08366c97eb8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1ad4d1ba6a0aa0489b7f2c80e0ffe59cd35b2e58
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904740"
---
# <a name="guid_array"></a>GUID_ARRAY
Kullanılabilir hata ayıklama motorları için benzersiz tanımlayıcıların dizisini açıklar.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagGUID_ARRAY
{
    DWORD dwCount;
    GUID *Members;
} GUID_ARRAY;
```

```csharp
public struct GUID_ARRAY
{
    public uint dwCount;
    public Guid Members;
}
```

## <a name="members"></a>Üyeler
`dwCount`\
Dizideki benzersiz tanımlayıcıların sayısı.

`Members`\
Benzersiz tanımlayıcılar içeren dizi.

## <a name="remarks"></a>Açıklamalar
Bu yapı [GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md) yöntemi tarafından döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)
