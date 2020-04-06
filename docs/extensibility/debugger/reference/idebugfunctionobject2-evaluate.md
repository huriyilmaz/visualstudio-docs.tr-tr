---
title: IDebugFunctionObject2::Değerlendirme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::Evaluate
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d87d7d3531d198a1478b4aaa55b354c3ac101302
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728440"
---
# <a name="idebugfunctionobject2evaluate"></a>IDebugFunctionObject2::Evaluate
İşlevi çağırır ve ortaya çıkan değeri nesne olarak döndürür.

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
[içinde] Giriş parametrelerini temsil eden [Bir IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesne dizisi. Bu parametrelerin her biri, bu arabirimdeki Oluşturma yöntemlerinden biri kullanılarak oluşturulmuştur.

`dwParams`\
[içinde] Dizideki `ppParams` parametrelerin sayısı.

`dwEvalFlags`\
[içinde] [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) numaralandırmasından değerlendirmenin nasıl yapılacağını belirten bayrakların birleşimi.

`dwTimeout`\
[içinde] Bu yöntemden dönmeden önce beklemek için milisaniye cinsinden en büyük süreyi belirtir. Sonsuza kadar beklemek için **SONSUZ** kullanın.

`ppResult`\
[çıkış] İşlevin nesne olarak değerini temsil eden bir **IDebugObject** döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
