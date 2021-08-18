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
ms.openlocfilehash: 5526282313c6cdc72fe3834e75855463036811e7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122088672"
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
[out] İşlevin değerini nesne olarak temsil eden bir [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) nesnesi tarafından temsil edilen işleve bir çağrı ayarlar ve yürütür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
