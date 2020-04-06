---
title: IDebugReference2::Karşılaştır | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::Compare
helpviewer_keywords:
- IDebugReference2::Compare
ms.assetid: 3361c495-2673-4b7c-82e3-dee74e1fa58d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0d293fcb89c92a19acc4f5a3910015914ef4231a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720646"
---
# <a name="idebugreference2compare"></a>IDebugReference2::Compare
Bir başvuruyla diğerini karşılaştırır. Daha sonraki kullanımlar için ayrılmıştır.

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
[içinde] Karşılaştırma işlemini belirten [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md) numaralandırmadeğeri, örneğin, eşit, daha az veya daha büyük.

`pReference`\
[içinde] Başvuruyu temsil eden bir [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) nesnesi karşılaştırılacak.

## <a name="return-value"></a>Dönüş Değeri
 Her zaman `E_NOTIMPL` döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)
