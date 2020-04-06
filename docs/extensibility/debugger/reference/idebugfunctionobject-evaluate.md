---
title: IDebugFunctionObject::Değerlendir | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::Evaluate
helpviewer_keywords:
- IDebugFunctionObject::Evaluate method
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 529a5f67c808efa258bc0cb9899f546dbb90d431
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728504"
---
# <a name="idebugfunctionobjectevaluate"></a>IDebugFunctionObject::Evaluate
İşlevi çağırır ve ortaya çıkan değeri nesne olarak döndürür.

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
[içinde] Giriş parametrelerini temsil eden [Bir IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesne dizisi. Bu parametrelerin her biri `Create` [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) arabirimindeki yöntemlerden biriyle oluşturulmuştur.

`dwParams`\
[içinde] Dizideki `ppParams` parametrelerin sayısı.

`dwTimeout`\
[içinde] Bu yöntemden dönmeden önce beklemek için milisaniye cinsinden en büyük süreyi belirtir. Süresiz beklemek için kullanın. `INFINITE`

`ppResult`\
[çıkış] İşlevin nesne olarak değerini temsil eden bir [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK döndürür; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) nesnesi tarafından temsil edilen işleve çağrı yıkıyor ve yürütür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
