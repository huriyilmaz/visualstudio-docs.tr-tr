---
description: IDebugFunctionObject::Evaluate işlevi çağırarak elde edilen değeri nesne olarak döndürür.
title: IDebugFunctionObject::Evaluate | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::Evaluate
helpviewer_keywords:
- IDebugFunctionObject::Evaluate method
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4bd3d7cae43ce8f49bdae121aca156490d5a197ebdb46c068c6167e79c2e6137
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121451997"
---
# <a name="idebugfunctionobjectevaluate"></a>IDebugFunctionObject::Evaluate
işlevini çağırarak elde edilen değeri nesne olarak döndürür.

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
[in] Giriş parametrelerini [temsil eden IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesneleri dizisi. Bu parametrelerin her biri `Create` [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) arabiriminde yöntemlerden biri ile oluşturulmuş.

`dwParams`\
[in] Dizide parametre `ppParams` sayısı.

`dwTimeout`\
[in] Bu yöntemden dönmeden önce bek için milisaniye cinsinden en uzun süreyi belirtir. Süresiz `INFINITE` olarak beklemek için kullanın.

`ppResult`\
[out] İşlevin değerini bir nesne olarak temsil eden [bir IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) nesnesi tarafından temsil edilen işleve bir çağrı ayarlar ve yürütür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
