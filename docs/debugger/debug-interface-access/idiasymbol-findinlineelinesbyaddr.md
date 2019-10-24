---
title: 'IDiaSymbol:: Findınlineelinesbyaddr | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f1ab47ca-c851-48ea-9c12-47fb80b31102
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1709120dfa8e115f4b14a4ee4e2d1c7ffb293329
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741217"
---
# <a name="idiasymbolfindinlineelinesbyaddr"></a>IDiaSymbol::findInlineeLinesByAddr
Bir istemcinin, belirtilen adres aralığı içinde Bu sembolde bulunan ve doğrudan veya dolaylı olarak satır numarası bilgilerini yinelemek için bir sabit listesi alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findInlineeLinesByAddr ( 
   DWORD                 isect,
   DWORD                 offset,
   DWORD                 length,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametreler
 `isect`

'ndaki Adresin bölüm bileşenini belirtir.

 `offset`

'ndaki Adresin konum bileşenini belirtir.

 `length`

'ndaki Bu sorguyla birlikte kapsamak üzere adres aralığını bayt cinsinden belirtir.

 `ppResult`

dışı Alınan satır numaralarının listesini içeren `IDiaEnumLineNumbers` nesnesini barındırır.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum Numaralandırması](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)