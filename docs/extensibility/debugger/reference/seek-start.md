---
title: SEEK_START | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SEEK_START
helpviewer_keywords:
- SEEK_START enumeration
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca1c38027123ca5147a6a7ab1fa6a3f92966409a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713595"
---
# <a name="seek_start"></a>SEEK_START
Sökme akışında aramaya başlayacağınız konumu belirtir.

## <a name="syntax"></a>Sözdizimi

```cpp
enum enum_SEEK_START { 
   SEEK_START_BEGIN       = 0x0001,
   SEEK_START_END         = 0x0002,
   SEEK_START_CURRENT     = 0x0003,
   SEEK_START_CODECONTEXT = 0x0004,
   SEEK_START_CODELOCID   = 0x0005
};
typedef DWORD SEEK_START;
```

```csharp
public enum enum_SEEK_START { 
   SEEK_START_BEGIN       = 0x0001,
   SEEK_START_END         = 0x0002,
   SEEK_START_CURRENT     = 0x0003,
   SEEK_START_CODECONTEXT = 0x0004,
   SEEK_START_CODELOCID   = 0x0005
};
```

## <a name="fields"></a>Alanlar
 `SEEK_START_BEGIN`\
 Geçerli belgenin başında aramaya başlar.

 `SEEK_START_END`\
 Geçerli belgenin sonunda aramaya başlar.

 `SEEK_START_CURRENT`\
 Geçerli belgenin geçerli konumunda aramaya başlar.

 `SEEK_START_CODECONTEXT`\
 Geçerli belgenin verilen kod bağlamında aramaya başlar.

 `SEEK_START_CODELOCID`\
 Verilen kod konum tanımlayıcısını aramaya başlar. Kod konum tanımlayıcıları [GetCurrentLocation'ı](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)arayarak elde edilir.

## <a name="remarks"></a>Açıklamalar
 [Arama](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) yöntemine bağımsız değişken olarak geçirilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
- [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)
