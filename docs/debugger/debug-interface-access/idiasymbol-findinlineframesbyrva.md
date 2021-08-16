---
description: IDiaSymbol::findInlineFramesByRVA, bir istemcinin belirtilen göreli sanal adresteki (RVA) tüm satır içi çerçeveler arasında yeniden işlemde bulunarak bir sabit adı alır.
title: IDiaSymbol::findInlineFramesByRVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: e7a6d9cb-2726-4ac7-9f38-415ad215bf9c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 532de406a97bffd9f48671a585971e4fccb6d028648d053a1de4c823c33bfbfa
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121404885"
---
# <a name="idiasymbolfindinlineframesbyrva"></a>IDiaSymbol::findInlineFramesByRVA
Bir istemcinin belirtilen bir göreli sanal adresteki (RVA) tüm satır içi çerçeveler üzerinde devamsını sağlayan bir sabit değer alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findInlineFramesByRVA (    DWORD             rva,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Parametreler
 `rva`

[in] Adresi RVA olarak belirtir.

 `ppResult`

[out] Alınan `IDiaEnumSymbols` çerçevelerin listesini içeren bir nesneyi tutar.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum Numaralandırması](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
