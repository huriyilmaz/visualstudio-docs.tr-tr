---
description: Hata ayıklayıcının üzerinde çalıştır olduğu bilgisayarı açıklar.
title: COMPUTER_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COMPUTER_INFO structure
ms.assetid: 943085b2-f165-462d-9a4e-2086f0cdfff4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 461ff8398617b75e54460288e40f82bcdcf4e0b4660c51ca514b078a47d7ef22
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121452439"
---
# <a name="computer_info"></a>COMPUTER_INFO
Hata ayıklayıcının üzerinde çalıştır olduğu bilgisayarı açıklar.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagCOMPUTER_INFO
{
    WORD wProcessorArchitecture;
    WORD wSuiteMask;
    DWORD dwOperatingSystemVersion;
} COMPUTER_INFO;
```

```csharp
public struct COMPUTER_INFO
{
    public ushort wProcessorArchitecture;
    public ushort wSuiteMask;
    public uint dwOperatingSystemVersion;
}
```

## <a name="members"></a>Üyeler
`wProcessorArchitecture`\
Mikro işlemcinin mimarisini tanımlar.

`wSuiteMask`\
Paket maskesini tanımlar.

`dwOperatingSystemVersion`\
İşletim sistemi sürüm numarası.

## <a name="remarks"></a>Açıklamalar
Bu yapı [GetComputerInfo yöntemi tarafından](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md) döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: Msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)
