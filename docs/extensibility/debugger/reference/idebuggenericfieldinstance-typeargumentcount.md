---
description: Bu örnek için tür parametresi bağımsız değişkenlerinin sayısını döndürür.
title: 'Idebuggenericfieldınstance:: TypeArgumentCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TypeArgumentCount
- IDebugGenericFieldInstance::TypeArgumentCount
ms.assetid: e662c5ea-a5c1-478e-a268-5980dadffcd1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c7afd914b3880ca1004a319a66b3f4176e15789e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072877"
---
# <a name="idebuggenericfieldinstancetypeargumentcount"></a>IDebugGenericFieldInstance::TypeArgumentCount
Bu örnek için tür parametresi bağımsız değişkenlerinin sayısını döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT TypeArgumentCount(
   ULONG32* pcArgs
);
```

```csharp
int TypeArgumentCount(
   ref uint pcArgs
);
```

## <a name="parameters"></a>Parametreler
`pcArgs`\
[in, out] Bu örnek için tür parametresi bağımsız değişkenlerinin sayısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Örneğin, liste ise \<int> , bu yöntem 1 değerini döndürür ve eğer liste \<int,float2> Bu yöntemin 2 değerini döndürürse. Bu yöntem, hiçbir tür bağımsız değişkeni yoksa 0 döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)
