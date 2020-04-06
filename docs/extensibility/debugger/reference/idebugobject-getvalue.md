---
title: IDebugObject::GetValue | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726545"
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
Nesnenin değerini ardışık bayt serisi olarak alır.

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
[içinde, dışarı] Nesnenin değerini temsil eden ardışık bayt dizisiyle doldurulmuş bir dizi.

`nSize`\
[içinde] Getirilen maksimum bayt sayısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK döndürür; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 [GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md) yöntemini arayarak getirilebilecek toplam değer bayt sayısını alın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
