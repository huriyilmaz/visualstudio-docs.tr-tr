---
description: Bu yöntem alan türünü alır.
title: 'IDebugField:: Getkinleştirilen d | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetKind
helpviewer_keywords:
- IDebugField::GetKind method
ms.assetid: e7c9c60a-8e55-4ecc-aa63-0c814a1e92cc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5e26f6850f8d0cdd1a197ec88a93ee1069d065bf
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077050"
---
# <a name="idebugfieldgetkind"></a>IDebugField::GetKind
Bu yöntem alan türünü alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetKind( 
   FIELD_KIND* pdwKind
);
```

```csharp
int GetKind(
   out enum_FIELD_KIND pdwKind
);
```

## <a name="parameters"></a>Parametreler
`pdwKind`\
dışı [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) sabitlerin bir birleşimi olarak alan türünü döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)
