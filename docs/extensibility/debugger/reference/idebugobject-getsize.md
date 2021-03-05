---
description: Nesnenin boyutunu bayt cinsinden alır.
title: 'IDebugObject:: GetSize | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetSize
helpviewer_keywords:
- IDebugObject::GetSize method
ms.assetid: 89af423b-36eb-479d-b2de-2693455eca15
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 69d644cb86c0df592218a5f6c90b8c2b62339718
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159984"
---
# <a name="idebugobjectgetsize"></a>IDebugObject::GetSize
Nesnenin boyutunu bayt cinsinden alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetSize( 
   UINT* pnSize
);
```

```csharp
int GetSize(
   out uint pnSize
);
```

## <a name="parameters"></a>Parametreler
`pnSize`\
dışı Bayt cinsinden boyutu döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Değeri bir bayt dizisi olarak almak için [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md) yöntemini kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
