---
title: SEEK_START | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713595"
---
# <a name="seek_start"></a>SEEK_START
Ayrıştırılmış bir akışta arama başlatma konumunu belirtir.

## <a name="syntax"></a>Syntax

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
 Geçerli belgenin başlangıcında aramayı başlatır.

 `SEEK_START_END`\
 Geçerli belgenin sonunda aramayı başlatır.

 `SEEK_START_CURRENT`\
 Geçerli belgenin geçerli konumunda aramayı başlatır.

 `SEEK_START_CODECONTEXT`\
 Geçerli belgenin verilen kod bağlamına aramayı başlatır.

 `SEEK_START_CODELOCID`\
 Belirtilen kod konumu tanımlayıcıda aramayı başlatır. Kod konumu tanımlayıcıları, [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)çağırarak elde edilir.

## <a name="remarks"></a>Açıklamalar
 [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) yöntemine bir bağımsız değişken olarak geçirilir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırmalar](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
- [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)
