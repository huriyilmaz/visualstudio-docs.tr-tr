---
description: Bu yöntem, varsa bir nesneyle ilişkili özel durumu alır.
title: 'IDebugBinder3:: GetExceptionObjectAndType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetExceptionObjectAndType
helpviewer_keywords:
- IDebugBinder3::GetExceptionObjectAndType method
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 67f6c146182546f83782a0299c0ea3e29f94a3b2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094256"
---
# <a name="idebugbinder3getexceptionobjectandtype"></a>IDebugBinder3::GetExceptionObjectAndType
Bu yöntem, varsa bir nesneyle ilişkili özel durumu alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetExceptionObjectAndType(
   IDebugObject** ppException,
   IDebugField**  ppField
);
```

```csharp
int GetExceptionObjectAndType(
   out IDebugObject ppException,
   out IDebugField  ppField
);
```

## <a name="parameters"></a>Parametreler
`ppException`\
dışı Özel durumu temsil eden nesneyi döndürür.

`ppField`\
dışı Özel duruma neden olmuş olabilecek belirli bir alanı temsil eden nesneyi döndürür (Bu bir null değer olabilir).

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

> [!NOTE]
> Bir özel durum olup olmadığını doğrulamak için, tarafından döndürülen değeri denetleyin `ppException` : null bir değer ise, bu nesneyle ilişkili bir özel durum yoktur.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
