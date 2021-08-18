---
description: IDiaSymbol::findInlineeLinesByAddr, bir istemcinin belirtilen adres aralığındaki bu sembolde satır içi, doğrudan veya dolaylı olarak tüm işlevlerin satır numarası bilgileri arasında bir sabitlevasyonu almalarına olanak sağlar.
title: IDiaSymbol::findInlineeLinesByAddr | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: f1ab47ca-c851-48ea-9c12-47fb80b31102
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 57eb156d96d20f1c1032980c31309c93519ab844
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122036282"
---
# <a name="idiasymbolfindinlineelinesbyaddr"></a>IDiaSymbol::findInlineeLinesByAddr
Bir istemcinin, belirtilen adres aralığındaki bu sembolde satır içine alınan, doğrudan veya dolaylı olarak tüm işlevlerin satır numarası bilgileri arasında bir numaralandırarak bir numaralandırıcısını verir.

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

[in] Adresin bölüm bileşenini belirtir.

 `offset`

[in] Adresin kaydırma bileşenini belirtir.

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
