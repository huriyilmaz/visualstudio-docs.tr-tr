---
title: 'IEEDataStorage:: GetSize | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetSize
helpviewer_keywords:
- IEEDataStorage::GetSize
ms.assetid: 33d232c4-1239-4abc-922b-e1bc5b908169
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2a18ae08500bd457f6e9ab316514836a30538a42
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965518"
---
# <a name="ieedatastoragegetsize"></a>IEEDataStorage::GetSize
Bu nesnede bulunan bayt sayısını döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetSize(
   ULONG* size
);
```

```csharp
int GetSize(
   out uint size
);
```

## <a name="parameters"></a>Parametreler
`size`\
dışı Bu nesnede bulunan baytların sayısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Asıl veri baytlarını almak için [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md) yöntemini kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [Veri Al](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)
