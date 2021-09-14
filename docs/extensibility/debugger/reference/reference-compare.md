---
description: Başvurular için karşılaştırma türünü belirtir.
title: REFERENCE_COMPARE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- REFERENCE_COMPARE
helpviewer_keywords:
- REFERENCE_COMPARE enumeration
ms.assetid: e31cdc78-f621-498b-9ca4-aefa790b9f6f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 419eb3927b0ee857f2a42234dae22bd605943f1a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726954"
---
# <a name="reference_compare"></a>REFERENCE_COMPARE
Başvurular için karşılaştırma türünü belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_REFERENCE_COMPARE { 
   REF_COMPARE_EQUAL        = 0x0001,
   REF_COMPARE_LESS_THAN    = 0x0002,
   REF_COMPARE_GREATER_THAN = 0x0003
};
typedef DWORD REFERENCE_COMPARE;
```

```csharp
public enum enum_REFERENCE_COMPARE { 
   REF_COMPARE_EQUAL        = 0x0001,
   REF_COMPARE_LESS_THAN    = 0x0002,
   REF_COMPARE_GREATER_THAN = 0x0003
};
```

## <a name="fields"></a>Alanlar
 `REF_COMPARE_EQUAL`\
 Eşit karşılaştırma belirtir.

 `REF_COMPARE_LESS_THAN`\
 Daha az karşılaştırma belirtir.

 `REF_COMPARE_GREATER_THAN`\
 Karşılaştırmadan büyük bir değer belirtir.

## <a name="remarks"></a>Açıklamalar
 Karşılaştırma yöntemine bağımsız değişken [olarak](../../../extensibility/debugger/reference/idebugreference2-compare.md) geçirildi.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Karşılaştır](../../../extensibility/debugger/reference/idebugreference2-compare.md)
