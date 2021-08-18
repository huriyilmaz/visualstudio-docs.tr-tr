---
description: Nesnenin değerini ardışık bir bayt dizisinde ayarlar.
title: IDebugObject::SetValue | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 68e2f923088ce16958ffbcd197baaf76f16c5733
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122034883"
---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
Nesnenin değerini ardışık bir bayt dizisinde ayarlar.

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
[in] Yeni değeri temsil eden bayt dizisi.

`nSize`\
[in] Değerin bayt cinsinden boyutu.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Dizide yer alan değerler bu [IDebugObject nesnesine](../../../extensibility/debugger/reference/idebugobject.md) kopyalanır ve mevcut değerlerin yerini alır. Yeni değerin boyutu mevcut değerden daha büyük veya daha küçük olabilir. Bu `IDebugObject` bir null başvuru olamaz.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
