---
description: Bir başvuruyu diğerine karşılaştırır.
title: 'IDebugReference2:: Compare | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::Compare
helpviewer_keywords:
- IDebugReference2::Compare
ms.assetid: 3361c495-2673-4b7c-82e3-dee74e1fa58d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e56b2d5883e1c26fbfaa8657b8fed3c5236db348
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725155"
---
# <a name="idebugreference2compare"></a>IDebugReference2::Compare
Bir başvuruyu diğerine karşılaştırır. Daha sonraki kullanımlar için ayrılmıştır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Compare ( 
   REFERENCE_COMPARE dwCompare,
   IDebugReference2* pReference
);
```

```csharp
int Compare ( 
   enum_REFERENCE_COMPARE dwCompare,
   IDebugReference2       pReference
);
```

## <a name="parameters"></a>Parametreler
`dwCompare`\
'ndaki Karşılaştırma işlemini belirten [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md) numaralandırmasından bir değer, örneğin, eşittir, küçüktür veya büyüktür.

`pReference`\
'ndaki Karşılaştırılacak başvuruyu temsil eden bir [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Her zaman `E_NOTIMPL` döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)
