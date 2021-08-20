---
description: Bu nesnede bulunan bayt sayısını döndürür.
title: 'IEEDataStorage:: GetSize | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetSize
helpviewer_keywords:
- IEEDataStorage::GetSize
ms.assetid: 33d232c4-1239-4abc-922b-e1bc5b908169
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0b0de358f2f207da7586c09be094ec14f6dadfbf
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122095796"
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
