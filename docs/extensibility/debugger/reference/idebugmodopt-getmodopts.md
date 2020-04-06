---
title: IDebugModOpt::GetModOpts | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt::GetModOpts
- GetModOpts
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5ab870db3ae3517b60bebd4815e4530f6035b327
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727056"
---
# <a name="idebugmodoptgetmodopts"></a>IDebugModOpt::GetModOpts
İsteğe bağlı değiştiriciler listesini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetModOpts(
   ULONG  celt,
   BSTR*  rgelt,
   ULONG* pceltFetched
);
```

```csharp
int GetModOpts(
   uint         celt,
   out string[] rgelt,
   ref uint     pceltFetched
);
```

## <a name="parameters"></a>Parametreler
`celt`\
[içinde] Döndürülecek öğe sayısı.

`rgelt`\
[çıkış] Seçenekleri içeren bir dizi döndürür.

`pceltFetched`\
[içinde, dışarı] `rgelt` Dizide döndürülen öğe sayısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)
