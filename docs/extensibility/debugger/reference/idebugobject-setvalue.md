---
description: Nesnenin değerini ardışık bir bayt dizisinden ayarlar.
title: 'IDebugObject:: SetValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetValue
helpviewer_keywords:
- IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 63d75eae9c7966bfc5e7fceea0512db0fa174066
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054107"
---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
Nesnenin değerini ardışık bir bayt dizisinden ayarlar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT SetValue( 
   BYTE* pValue,
   UINT  nSize
);
```

```csharp
int SetValue(
   byte[] pValue,
   uint   nSize
);
```

## <a name="parameters"></a>Parametreler
`pValue`\
'ndaki Yeni değeri temsil eden bir bayt dizisi.

`nSize`\
'ndaki Değerin bayt cinsinden boyutu.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Dizideki değerler bu [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesnesine kopyalanır ve var olan tüm değerleri değiştirir. Yeni değerin boyutu mevcut değerden daha büyük veya daha küçük olabilir. Bu `IDebugObject` bir null başvuru olamaz.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
