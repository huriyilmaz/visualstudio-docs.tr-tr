---
description: İsteğe bağlı değiştiricilerin bir listesini alır.
title: 'Idebugmodopt:: GetModOpts | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt::GetModOpts
- GetModOpts
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c13c664e80fe0ea2d479911d75fbd62b5d51e97b143fcd1cd89144718a5ede86
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121433638"
---
# <a name="idebugmodoptgetmodopts"></a>IDebugModOpt::GetModOpts
İsteğe bağlı değiştiricilerin bir listesini alır.

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
'ndaki Döndürülecek öğe sayısı.

`rgelt`\
dışı Seçenekleri içeren bir dizi döndürür.

`pceltFetched`\
[in, out] Dizide döndürülen öğe sayısı `rgelt` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)
