---
title: 'IDebugObject:: GetValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 45d555cbea6bf8239ef4527ba982072e17532af4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726545"
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
Nesnenin değerini ardışık bir bayt dizisi olarak alır.

## <a name="syntax"></a>Söz dizimi

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
