---
description: IDiaSession::findInlineeLinesByAddr, bir istemcinin, belirtilen üst simge tarafından satır içi, doğrudan veya dolaylı olarak tüm işlevlerin satır numarası bilgileri arasında bir numaralandırarak, belirtilen adres aralığında yer alan bir sabit adı verir.
title: IDiaSession::findInlineeLinesByAddr | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: bb70e408-eed1-4c9c-b5b1-44323125f48b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f8a8c4b8ccf42012557d87581c212cea95cda552
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122081384"
---
# <a name="idiasessionfindinlineelinesbyaddr"></a>IDiaSession::findInlineeLinesByAddr
Bir istemcinin, belirtilen üst simge tarafından satır içine alınan, doğrudan veya dolaylı olarak tüm işlevlerin satır numarası bilgileri arasında ve belirtilen adres aralığında yer alan tüm işlevlerin satır numarası bilgileri arasında bir numaralandırarak bir numaralandırır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findInlineeLinesByAddr ( 
   IDiaSymbol*           parent,   DWORD                 isect,   DWORD                 offset,   DWORD                 length,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametreler
 `parent`

[in] Üst `IDiaSymbol` öğeyi temsil eden nesne.

 `isect`

[in] Adresin bölüm bileşenini belirtir.

 `offset`

[in] Adresin uzaklık bileşenini belirtir.

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
