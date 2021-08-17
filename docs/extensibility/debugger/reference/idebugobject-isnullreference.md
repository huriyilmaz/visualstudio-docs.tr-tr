---
description: Bu nesnenin null bir başvuru olup olmadığını sınar.
title: 'IDebugObject:: ısnullreference | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsNullReference
helpviewer_keywords:
- IDebugObject::IsNullReference method
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dbc163532bf1f41327d3d9615f6fdf9a1bd3b320
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122088503"
---
# <a name="idebugobjectisnullreference"></a>IDebugObject::IsNullReference
Bu nesnenin null bir başvuru olup olmadığını sınar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT IsNullReference( 
   BOOL* pfIsNull
);
```

```csharp
int IsNullReference(
   out int pfIsNull
);
```

## <a name="parameters"></a>Parametreler
`pfIsNull`\
dışı `TRUE`Bu nesne null bir başvuru ise sıfır olmayan () döndürür; Aksi takdirde, sıfır () döndürür `FALSE` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Null başvuru, boş bir nesne veya atanmamış bir nesne anlamına gelir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
