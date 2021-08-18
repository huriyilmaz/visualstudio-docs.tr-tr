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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5c9ab356a50a7132d1e10d170a98d8ee6491a29e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122035065"
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
