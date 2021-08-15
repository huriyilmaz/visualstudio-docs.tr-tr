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
ms.openlocfilehash: 4c96dd0ec84c88039155300cca19c8b36e3fa8d39245a78343347a368ed82379
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121433482"
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
