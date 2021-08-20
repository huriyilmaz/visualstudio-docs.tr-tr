---
description: Bir ayrık akışta aramaya başlama konumunu belirtir.
title: SEEK_START | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SEEK_START
helpviewer_keywords:
- SEEK_START enumeration
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a7940ca7689da1dab20141191489800c2a3810c3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122125237"
---
# <a name="seek_start"></a>SEEK_START
Bir ayrık akışta aramaya başlama konumunu belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_SEEK_START { 
   SEEK_START_BEGIN       = 0x0001,
   SEEK_START_END         = 0x0002,
   SEEK_START_CURRENT     = 0x0003,
   SEEK_START_CODECONTEXT = 0x0004,
   SEEK_START_CODELOCID   = 0x0005
};
typedef DWORD SEEK_START;
```

```csharp
public enum enum_SEEK_START { 
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
 Verilen kod konumu tanımlayıcısında aramaya başlar. Kod konumu tanımlayıcıları [GetCurrentLocation çağrılarak elde edilir.](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)

## <a name="remarks"></a>Açıklamalar
 Seek yöntemine bağımsız değişken [olarak](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) geçirildi.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
- [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)
