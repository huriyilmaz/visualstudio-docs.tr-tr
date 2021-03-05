---
description: Bir istemcinin, Bu sembolde doğrudan veya dolaylı olarak, satır numarası bilgileri üzerinden yineleme yapmasına izin veren bir sabit listesi alır.
title: 'IDiaSymbol:: findInlineeLines | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 56ba4bc0-8f96-47c2-8b18-332b4e7c2d91
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f2e590c70da50a9c316bdad99cee4e4cb056312d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156785"
---
# <a name="idiasymbolfindinlineelines"></a>IDiaSymbol::findInlineeLines
Bir istemcinin, Bu sembolde doğrudan veya dolaylı olarak, satır numarası bilgileri üzerinden yineleme yapmasına izin veren bir sabit listesi alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findInlineeLines ( 
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametreler
 `ppResult`

dışı `IDiaEnumLineNumbers` Alınan satır numaralarının listesini içeren bir nesnesi tutar.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum Numaralandırması](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)
