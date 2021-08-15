---
description: Dize dizisini açıklayan bir yapı.
title: BSTR_ARRAY | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BSTR_ARRAY
helpviewer_keywords:
- BSTR_ARRAY structure
ms.assetid: 48da37f7-a237-48a9-9ff9-389c1a00862c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a84ec868a7bd2aaa6cd1326e08b0b8a869b7311672cbfeca47e584c723a95a68
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121262691"
---
# <a name="bstr_array"></a>BSTR_ARRAY
Dize dizisini açıklayan bir yapı.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagBSTR_ARRAY {
    DWORD dwCount;
    BSTR* Members;
} BSTR_ARRAY;
```

```csharp
struct BSTR_ARRAY {
    DWORD    dwCount;
    string[] Members;
}
```

## <a name="members"></a>Üyeler
`dwCount`\
Dizide dize `Members` sayısı.

`Members`\
Dize dizisi.

## <a name="remarks"></a>Açıklamalar
Bu yapı [EnumPersistedPorts yönteminden](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) döndürülür.

 [yalnızca C++ ] Her bir dizenin kullanılarak serbest `SysFreeString` bırakılası `Members` ve dizisi ile serbest bırak bırak bırakıladır. `CoTaskMemFree`

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)
