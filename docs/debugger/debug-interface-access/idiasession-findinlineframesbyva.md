---
title: 'IDiaSession:: findInlineFramesByVA | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: df9e68f6-e0a4-4cf6-b11d-61c40351e0cd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dca26021909220f9bb68a6794c299ec6c5a3d75a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742139"
---
# <a name="idiasessionfindinlineframesbyva"></a>IDiaSession::findInlineFramesByVA
Bir istemcinin belirtilen bir sanal adresteki (VA) tüm satır içi çerçevelerde yineleme yapmasına izin veren bir sabit listesi alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findInlineFramesByVA ( 
   IDiaSymbol*       parent,   ULONGLONG         va,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Parametreler
 `parent`

'ndaki Üst öğeyi temsil eden `IDiaSymbol` nesne.

 `va`

'ndaki Adresi bir VA olarak belirtir.

 `ppResult`

dışı Alınan çerçevelerin listesini içeren `IDiaEnumSymbols` nesnesini barındırır.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum Numaralandırması](../../debugger/debug-interface-access/symtagenum.md)