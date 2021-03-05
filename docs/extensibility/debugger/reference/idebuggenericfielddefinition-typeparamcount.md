---
description: Genel alanla ilişkili tür parametrelerinin sayısını alır.
title: 'Idebuggenericfielddefinition:: TypeParamCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TypeParamCount
- IDebugGenericFieldDefinition::TypeParamCount
ms.assetid: d41dd5ea-aa25-4bf3-bcfd-e0bf451ead49
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6ca50847ca5eb6538cfb4852a4543e02ab4c1fc0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165468"
---
# <a name="idebuggenericfielddefinitiontypeparamcount"></a>IDebugGenericFieldDefinition::TypeParamCount
Genel alanla ilişkili tür parametrelerinin sayısını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT TypeParamCount(
   ULONG32* pcParams
);
```

```csharp
int TypeParamCount(
   ref uint pcParams
);
```

## <a name="parameters"></a>Parametreler
`pcParams`\
[in, out] Tür parametrelerinin sayısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Liste ise \<T> , bu yöntem 1 döndürür ve eğer liste ise \<T1,T2> , bu yöntem 2 değerini döndürür. Bu yöntem, hiçbir tür parametresi yoksa 0 döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)
