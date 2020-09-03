---
title: 'IDebugObject:: SetValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetValue
helpviewer_keywords:
- IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9e4652eb3c77a1871063dfa71b464fb1f7c43f94
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726362"
---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
Nesnenin değerini ardışık bir bayt dizisinden ayarlar.

## <a name="syntax"></a>Söz dizimi

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
