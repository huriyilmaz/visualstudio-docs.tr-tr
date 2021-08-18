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
ms.openlocfilehash: 94e49ed1f72cd5477becc6a41abb10635d03805a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122145659"
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
