---
description: IDiaSymbol::findInlineFramesByAddr, bir istemcinin belirli bir adresteki tüm satır içi çerçeveler arasında devam eden bir sabit adı verir.
title: IDiaSymbol::findInlineFramesByAddr | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 36a122e6-f27e-40cd-9784-cdaf279e1905
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: e8d9577bb9dc04dd8d226303ff149f2a40fe37c8
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626744"
---
# <a name="idiasymbolfindinlineframesbyaddr"></a>IDiaSymbol::findInlineFramesByAddr
bir istemcinin belirli bir adresteki tüm satır içi çerçeveler üzerinde devamsını sağlayan bir sabit adı verir.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findInlineFramesByAddr ( 
   DWORD             isect,
   DWORD             offset,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Parametreler
 `isect`

[in] Adresin bölüm bileşenini belirtir.

 `offset`

[in] Adresin uzaklık bileşenini belirtir.

 `ppResult`

[out] Alınan `IDiaEnumSymbols` çerçevelerin listesini içeren bir nesneyi tutar.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum Numaralandırması](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
