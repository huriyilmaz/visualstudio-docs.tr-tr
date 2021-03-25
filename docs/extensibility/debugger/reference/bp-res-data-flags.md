---
description: Veri kesme noktasının donanımda öykünmesinin yapılıp yapılmayacağını veya uygulanıp uygulanmadığını belirtir.
title: BP_RES_DATA_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RES_DATA_FLAGS
helpviewer_keywords:
- BP_RES_DATA_FLAGS enumeration
ms.assetid: d97611e2-def6-45a9-ad7d-eedf2ad4c82b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 293b3635dd1a725f90ce63a0aa2f8568d5b324e3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078181"
---
# <a name="bp_res_data_flags"></a>BP_RES_DATA_FLAGS
Veri kesme noktasının donanımda öykünmesinin yapılıp yapılmayacağını veya uygulanıp uygulanmadığını belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BP_RES_DATA_FLAGS {
    BP_RES_DATA_EMULATED = 0x0001
};
typedef DWORD BP_RES_DATA_FLAGS;
```

```csharp
public enum enum_BP_RES_DATA_FLAGS {
    BP_RES_DATA_EMULATED = 0x0001
};
```

## <a name="fields"></a>Alanlar
`BP_RES_DATA_EMULATED`\
Veri kesme noktasının öykünmekte olduğunu belirtir.

## <a name="remarks"></a>Açıklamalar
`dwFlags` [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) yapısının üyesi için kullanılır.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)
