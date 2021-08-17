---
description: IDiaSession::findInlineeLinesByRVA, bir istemcinin, belirtilen üst simge tarafından satır içi, doğrudan veya dolaylı olarak tüm işlevlerin satır numarası bilgisinde ve belirtilen göreli sanal adres (RVA) içinde yer alan tüm işlevlerin satır numarası bilgileri arasında bir numaralama alır.
title: IDiaSession::findInlineeLinesByRVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 7a74d5ee-0dbf-47c0-92b4-47ec03b13ce9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 1bb42c5d1ffed49c8bff3a6bc23f20f3cb9c86d5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122044297"
---
# <a name="idiasessionfindinlineelinesbyrva"></a>IDiaSession::findInlineeLinesByRVA
Bir istemcinin, belirtilen üst simge tarafından satır içine alınan, doğrudan veya dolaylı olarak tüm işlevlerin satır numarası bilgileri arasında ve belirtilen göreli sanal adres (RVA) içinde yer alan tüm işlevlerin satır numarası bilgileri arasında bir numaralandırarak alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findInlineeLinesByRVA ( 
   IDiaSymbol*           parent,
   DWORD                 rva,
   DWORD                 length,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametreler
 `parent`

[in] Üst `IDiaSymbol` öğeyi temsil eden nesne.

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
