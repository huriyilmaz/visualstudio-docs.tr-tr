---
description: IDiaSymbol::findInlineeLinesByRVA, bir istemcinin, belirtilen göreli sanal adres (RVA) içindeki bu simgede satır içi, doğrudan veya dolaylı olarak tüm işlevlerin satır numarası bilgileri arasında devam eden bir sabit adı alır.
title: IDiaSymbol::findInlineeLinesByRVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: ac108db1-9dbf-4dc4-bf48-159ca8d3725c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: d0d1d7b83dd8e643dc5d25d71d43b50c039a8b25
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626745"
---
# <a name="idiasymbolfindinlineelinesbyrva"></a>IDiaSymbol::findInlineeLinesByRVA
Bir istemcinin, belirtilen göreli sanal adres (RVA) içindeki bu simgede satır içine alınan, doğrudan veya dolaylı olarak tüm işlevlerin satır numarası bilgileri arasında bir numaralandırarak bir numaralandırarak alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findInlineeLinesByRVA (    DWORD                 rva,   DWORD                 length,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametreler
 `rva`

[in] Adresi RVA olarak belirtir.

 `length`

[in] Bu sorguyu kapsayacak adres aralığını bayt sayısı cinsinden belirtir.

 `ppResult`

[out] Alınan `IDiaEnumLineNumbers` satır numaralarının listesini içeren bir nesneyi tutar.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum Numaralandırması](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)
