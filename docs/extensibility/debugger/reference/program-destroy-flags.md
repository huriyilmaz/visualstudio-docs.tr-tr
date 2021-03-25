---
description: Program yok etme bayraklarının geçerli değerlerini numaralandırır.
title: PROGRAM_DESTROY_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- PROGRAM_DESTROY_FLAGS enumeration
ms.assetid: be00d4a3-d5b8-4159-b632-64577f534883
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7abe750e76fa7cfcbecfd8b82853aeccbe543352
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079624"
---
# <a name="program_destroy_flags"></a>PROGRAM_DESTROY_FLAGS
Program yok etme bayraklarının geçerli değerlerini numaralandırır.

## <a name="syntax"></a>Syntax

```cpp
enum enum_PPROGRAM_DESTROY_FLAGS
{
   PROGRAM_DESTROY_CONTINUE_DEBUGGING = 0x1
};
typedef DWORD PROGRAM_DESTROY_FLAGS;
```

```csharp
public enum enum_PPROGRAM_DESTROY_FLAGS
{
   PROGRAM_DESTROY_CONTINUE_DEBUGGING = 0x1
};
```

## <a name="fields"></a>Alanlar
 `PROGRAM_DESTROY_CONTINUE_DEBUGGING`\
 Programı yok edin, ancak hata ayıklamaya devam edin.

## <a name="remarks"></a>Açıklamalar
 Sabit listesi [GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md) yöntemi tarafından döndürülür.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)
