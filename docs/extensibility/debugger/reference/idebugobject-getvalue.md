---
description: Nesnenin değerini ardışık bir bayt dizisi olarak alır.
title: 'IDebugObject:: GetValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d957743a725ad462a9ed95fca6ebdffbecb6de16
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054133"
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
Nesnenin değerini ardışık bir bayt dizisi olarak alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetValue( 
   BYTE* pValue,
   UINT  nSize
);
```

```csharp
int GetValue(
   ref byte[] pValue,
   uint nSize
);
```

## <a name="parameters"></a>Parametreler
`pValue`\
[in, out] Nesnenin değerini temsil eden ardışık bir bayt serisi ile doldurulmuş dizi.

`nSize`\
'ndaki Getirilecek en fazla bayt sayısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 [GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md) yöntemi çağırarak getirilen toplam değer baytı sayısını alır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
