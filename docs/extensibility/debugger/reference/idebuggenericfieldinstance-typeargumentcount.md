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
ms.openlocfilehash: e36f631f879ddaa8de6db2c69388ee709c7044330c4a9b2b7bef929b8271db4e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121402693"
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
