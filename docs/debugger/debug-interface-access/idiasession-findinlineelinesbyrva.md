---
description: 'IDiaSession:: Findınlineelinesbyrva, bir istemcinin belirtilen ana sembolüyle doğrudan veya dolaylı olarak satır numarası bilgilerini, belirtilen üst simgeye sahip olduğunu ve belirtilen göreli sanal adres (RVA) içinde yer aldığı bir sabit listesi alır.'
title: 'IDiaSession:: findInlineeLinesByRVA | Microsoft Docs'
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
ms.openlocfilehash: 62997b528ff7814dee765a5b3408a576419332994e5463a132f42556f183cb6f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121391827"
---
# <a name="idiasessionfindinlineelinesbyrva"></a>IDiaSession::findInlineeLinesByRVA
Bir istemcinin, belirtilen ana sembolüyle doğrudan veya dolaylı olarak satır numarası bilgileri üzerinden yineleyebilir ve belirtilen göreli sanal adres (RVA) içinde yer alır.

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

'ndaki `IDiaSymbol` Üst öğeyi temsil eden nesne.

 `rva`

'ndaki Adresi RVA olarak belirtir.

 `length`

'ndaki Bu sorguyla birlikte kapsamak üzere adres aralığını bayt cinsinden belirtir.

 `ppResult`

dışı `IDiaEnumLineNumbers` Alınan satır numaralarının listesini içeren bir nesnesi tutar.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum Numaralandırması](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
