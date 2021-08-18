---
description: Göreli sanal adres (RVA) ile bir arama gerçekleştirerek numaralandırıcısı konumlandırır.
title: 'IDiaEnumSymbolsByAddr:: symbolByRVA | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::symbolByRVA method
ms.assetid: f7828029-f2ee-4ccd-afac-785adc60a4c8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f223845e1d83a1f12c58973fa6ccb644b9902b8a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122134420"
---
# <a name="idiaenumsymbolsbyaddrsymbolbyrva"></a>IDiaEnumSymbolsByAddr::symbolByRVA
Göreli sanal adres (RVA) ile bir arama gerçekleştirerek numaralandırıcısı konumlandırır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT symbolByRVA ( 
   DWORD**      relativeVirtualAddress,
   IDiaSymbol** ppsymbol
);
```

#### <a name="parameters"></a>Parametreler
 relativeVirtualAddress

'ndaki Görüntünün başlangıcına göre adres.

 ppsymbol

dışı Bulunan simgeyi temsil eden bir [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Simgenin bulunamadıysanız, döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaEnumSymbolsByAddr::symbolByVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyva.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
