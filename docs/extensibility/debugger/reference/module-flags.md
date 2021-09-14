---
description: Bir modülü tanımlamakta kullanılır.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634777"
---
# <a name="module_flags"></a>MODULE_FLAGS
Bir modülü tanımlamakta kullanılır.

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
 Modül olmadığını belirtir.

 `MODULE_FLAG_SYSTEM`\
 Bir sistem modülünü belirtir.

 `MODULE_FLAG_SYMBOLS`\
 Bir sembol modülünü belirtir.

 `MODULE_FLAG_64BIT`\
 64 bitlik bir modül belirtir.

 `MODULE_FLAG_OPTIMIZED`\
 Modülün iyileştirildiğini belirtir. Bu durum **modüller** penceresinde yansıtılır.

 `MODULE_FLAG_UNOPTIMIZED`\
 Modülün iyileştirilmediğini belirtir. Bu durum **modüller** penceresinde yansıtılır. Bu, varsayılan durumdur.

## <a name="remarks"></a>Açıklamalar
 `m_dwModuleFlags` [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) yapısının üyesi için kullanılır.

 Bu bayraklar bit düzeyinde birleştirilebilir `OR` .

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
