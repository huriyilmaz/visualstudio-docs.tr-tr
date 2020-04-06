---
title: COMPUTER_INFO | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COMPUTER_INFO structure
ms.assetid: 943085b2-f165-462d-9a4e-2086f0cdfff4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 27794dff51646b72dbbfda81ead02e5206ade78b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737661"
---
# <a name="computer_info"></a>COMPUTER_INFO
Hata ayıklamanın çalıştırıldığı bilgisayarı açıklar.

## <a name="syntax"></a>Sözdizimi

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
Mikroişlemcinin mimarisini tanımlar.

`wSuiteMask`\
Süit maskesini tanımlar.

`dwOperatingSystemVersion`\
İşletim sistemi sürüm numarası.

## <a name="remarks"></a>Açıklamalar
Bu yapı [GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md) yöntemi ile döndürülür.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: Msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)
