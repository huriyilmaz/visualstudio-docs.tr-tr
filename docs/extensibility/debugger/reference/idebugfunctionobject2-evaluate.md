---
description: 'IDebugFunctionObject2:: değerlendir işlevi çağırır ve sonuç değerini bir nesne olarak döndürür.'
title: 'IDebugFunctionObject2:: değerlendir | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::Evaluate
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 777553e1889e751cf84f6e4c58691e0c5f446648
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166469"
---
# <a name="idebugfunctionobject2evaluate"></a>IDebugFunctionObject2::Evaluate
İşlevini çağırır ve sonuç değerini bir nesne olarak döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Evaluate (
   IDebugObject** ppParams,
   DWORD          dwParams,
   DWORD          dwEvalFlags,
   DWORD          dwTimeout,
   IDebugObject** ppResult
);
```

```csharp
int Evaluate (
   IDebugObject     ppParams,
   uint             dwParams,
   uint             dwEvalFlags,
   uint             dwTimeout,
   out IDebugObject ppResult
);
```

## <a name="parameters"></a>Parametreler
`ppParams`\
'ndaki Giriş parametrelerini temsil eden bir [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesneleri dizisi. Bu parametrelerin her biri, bu arabirimdeki Create yöntemlerinden biri kullanılarak oluşturulmuştur.

`dwParams`\
'ndaki Dizideki parametrelerin sayısı `ppParams` .

`dwEvalFlags`\
'ndaki [Evalflags](../../../extensibility/debugger/reference/evalflags.md) numaralandırmasındaki, değerlendirmenin nasıl gerçekleştirileceğini belirten bayrakların birleşimi.

`dwTimeout`\
'ndaki Bu yöntemden dönmeden önce beklenecek en uzun süreyi milisaniye olarak belirtir. Sonsuza kadar beklemek için **sonsuz** kullanın.

`ppResult`\
dışı İşlevin değerini bir nesne olarak temsil eden bir **IDebugObject** döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
