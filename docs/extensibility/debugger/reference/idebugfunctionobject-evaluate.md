---
description: 'IDebugFunctionObject:: değerlendir işlevi çağırır ve sonuç değerini bir nesne olarak döndürür.'
title: 'IDebugFunctionObject:: değerlendir | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::Evaluate
helpviewer_keywords:
- IDebugFunctionObject::Evaluate method
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d15cdb09de32edcdf6159567db12e05cffd06e7e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160114"
---
# <a name="idebugfunctionobjectevaluate"></a>IDebugFunctionObject::Evaluate
İşlevini çağırır ve sonuç değerini bir nesne olarak döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Evaluate( 
   IDebugObject** ppParams,
   DWORD          dwParams,
   DWORD          dwTimeout,
   IDebugObject** ppResult
);
```

```csharp
int Evaluate(
   IDebugObject[]   ppParams,
   IntPtr           dwParams,
   uint             dwTimeout,
   out IDebugObject ppResult
);
```

## <a name="parameters"></a>Parametreler
`ppParams`\
'ndaki Giriş parametrelerini temsil eden bir [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesneleri dizisi. Bu parametrelerin her biri `Create` [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) arabirimindeki yöntemlerden biriyle oluşturulmuştur.

`dwParams`\
'ndaki Dizideki parametrelerin sayısı `ppParams` .

`dwTimeout`\
'ndaki Bu yöntemden dönmeden önce beklenecek en uzun süreyi milisaniye olarak belirtir. `INFINITE`Sonsuza kadar beklemek için kullanın.

`ppResult`\
dışı İşlevin değerini bir nesne olarak temsil eden bir [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) nesnesinin temsil ettiği işleve bir çağrı yapar ve yürütülür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
