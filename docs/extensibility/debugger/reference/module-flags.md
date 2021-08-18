---
description: Bir modülü açıklamak için kullanılır.
title: MODULE_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 83aa45e4fdcac756dbd623abcb1203fa160c9820
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122110793"
---
# <a name="module_flags"></a>MODULE_FLAGS
Bir modülü açıklamak için kullanılır.

## <a name="syntax"></a>Syntax

```cpp
enum enum_MODULE_FLAGS { 
   MODULE_FLAG_NONE        = 0x0000,
   MODULE_FLAG_SYSTEM      = 0x0001,
   MODULE_FLAG_SYMBOLS     = 0x0002,
   MODULE_FLAG_64BIT       = 0x0004,
   MODULE_FLAG_OPTIMIZED   = 0x0008,
   MODULE_FLAG_UNOPTIMIZED = 0x0010
};
typedef DWORD MODULE_FLAGS;
```

```csharp
public enum enum_MODULE_FLAGS { 
   MODULE_FLAG_NONE        = 0x0000,
   MODULE_FLAG_SYSTEM      = 0x0001,
   MODULE_FLAG_SYMBOLS     = 0x0002,
   MODULE_FLAG_64BIT       = 0x0004,
   MODULE_FLAG_OPTIMIZED   = 0x0008,
   MODULE_FLAG_UNOPTIMIZED = 0x0010
};
```

## <a name="fields"></a>Alanlar
 `MODULE_FLAG_NONE`\
 Modül belirtir.

 `MODULE_FLAG_SYSTEM`\
 Sistem modülünü belirtir.

 `MODULE_FLAG_SYMBOLS`\
 Sembol modülünü belirtir.

 `MODULE_FLAG_64BIT`\
 64 bit modülü belirtir.

 `MODULE_FLAG_OPTIMIZED`\
 Modülün iyileştirilmiş olduğunu belirtir. Bu durum Modüller **penceresine yansıtıldı.**

 `MODULE_FLAG_UNOPTIMIZED`\
 Modülün en iyi duruma getirilmiş olmadığını belirtir. Bu durum Modüller **penceresine yansıtıldı.** Bu varsayılan durum olur.

## <a name="remarks"></a>Açıklamalar
 Bu `m_dwModuleFlags` yapının üyesi [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) kullanılır.

 Bu bayraklar bit olarak birleştirilmiş `OR` olabilir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
