---
description: Kullanılabilir hata ayıklama altyapıları için bir dizi benzersiz tanımlayıcıyı açıklar.
title: GUID_ARRAY | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GUID_ARRAY structure
ms.assetid: 9e12500c-2c1c-49b1-a0ba-e08366c97eb8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d0552a109d671e7162d8ec41a7022bbacbfa48c0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122064974"
---
# <a name="guid_array"></a>GUID_ARRAY
Kullanılabilir hata ayıklama altyapıları için bir dizi benzersiz tanımlayıcıyı açıklar.

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
Dizide benzersiz tanımlayıcıların sayısı.

`Members`\
Benzersiz tanımlayıcıları içeren dizi.

## <a name="remarks"></a>Açıklamalar
Bu yapı [GetEngineFilter yöntemi tarafından](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md) döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: Msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)
