---
title: IEnumDebugModules2::Sonraki | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2::Next
helpviewer_keywords:
- IEnumDebugModules2::Next
ms.assetid: 46b7ccad-b07b-4ec0-b3ce-13981ffab7e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7b4041f0082bb4a2789c9b9d707ad129f52f1f61
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716528"
---
# <a name="ienumdebugmodules2next"></a>IEnumDebugModules2::Next
Numaralandırmadan sonraki eleman kümesini döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Next(
   ULONG           celt,
   IDebugModule2** rgelt,
   ULONG*          pceltFetched
);
```

```csharp
int Next(
   uint            celt,
   IDebugModule2[] rgelt,
   ref uint        pceltFetched
);
```

## <a name="parameters"></a>Parametreler
`celt`\
[içinde] Alınacak öğe sayısı. Ayrıca `rgelt` dizinin en büyük boyutunu belirtir.

`rgelt`\
[içinde, dışarı] Doldurulacak [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) öğeleri dizisi.

`pceltFetched`\
[çıkış] Gerçekte döndürülen öğe sayısını `rgelt`döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döndürür. İstenen öğe sayısından daha az ise döndürür; `S_FALSE` aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
