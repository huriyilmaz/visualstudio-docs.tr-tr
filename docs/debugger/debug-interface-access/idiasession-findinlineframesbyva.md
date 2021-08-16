---
description: IDiaSession::findInlineFramesByVA, bir istemcinin belirtilen bir sanal adresteki (VA) tüm satır içi çerçeveler arasında devamını sağlayan bir sabit adı alır.
title: IDiaSession::findInlineFramesByVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: df9e68f6-e0a4-4cf6-b11d-61c40351e0cd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ea39013ba5825f3607c743c48c04b35a66547dceb1210106ba2244f99e646b8d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121380313"
---
# <a name="idiasessionfindinlineframesbyva"></a>IDiaSession::findInlineFramesByVA
Bir istemcinin belirtilen bir sanal adresteki (VA) tüm satır içi çerçeveler üzerinde devamını sağlayan bir sabit adı alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findInlineFramesByVA ( 
   IDiaSymbol*       parent,   ULONGLONG         va,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Parametreler
 `parent`

[in] Üst `IDiaSymbol` öğeyi temsil eden nesne.

 `va`

[in] Adresi VA olarak belirtir.

 `ppResult`

[out] Alınan `IDiaEnumSymbols` çerçevelerin listesini içeren bir nesneyi tutar.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum Numaralandırması](../../debugger/debug-interface-access/symtagenum.md)
