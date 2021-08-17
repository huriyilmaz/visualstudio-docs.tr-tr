---
description: 'IDiaSession:: Findınlineelinesbyva, bir istemcinin belirtilen ana sembolüyle doğrudan veya dolaylı olarak satır numarası bilgileri üzerinden yineleme yapmasına izin veren bir sabit listesi alır ve belirtilen sanal adreste (VA) bulunur.'
title: 'IDiaSession:: findInlineeLinesByVA | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: dffe6594-e0d1-4ed5-aeea-8773f88d82a6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7b14bbe058ef074d8173d5c11b37130abf576d9a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122105558"
---
# <a name="idiasessionfindinlineelinesbyva"></a>IDiaSession::findInlineeLinesByVA
Bir istemcinin, belirtilen ana sembolüyle doğrudan veya dolaylı olarak satır numarası bilgileri üzerinden yineleme yapmasına izin veren ve belirtilen sanal adres (VA) içinde yer alan bir sabit listesi alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findInlineeLinesByVA ( 
   IDiaSymbol*           parent,   ULONGLONG             va,   DWORD                 length,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametreler
 `parent`

'ndaki `IDiaSymbol` Üst öğeyi temsil eden nesne.

 `va`

'ndaki Adresi bir VA olarak belirtir.

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
