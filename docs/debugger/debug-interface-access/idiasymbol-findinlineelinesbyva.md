---
description: 'IDiaSymbol:: Findınlineelinesbyva, bir istemcinin belirtilen sanal adres (VA) içindeki Bu sembolde yer alan ve doğrudan veya dolaylı olarak satır numarası bilgilerini yinelemesinden izin veren bir sabit listesi alır.'
title: 'IDiaSymbol:: findInlineeLinesByVA | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 61427d33-30d2-4ac9-9bd6-c58c6c705072
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c734fb46b759160e4424da97cb00dd6a97bd559e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122097791"
---
# <a name="idiasymbolfindinlineelinesbyva"></a>IDiaSymbol::findInlineeLinesByVA
Bir istemcinin, belirtilen sanal adres (VA) içindeki Bu sembolde yer alan ve doğrudan veya dolaylı olarak satır numarası bilgilerini yinelemesinden izin veren bir sabit listesi alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findInlineeLinesByVA ( 
   ULONGLONG             va,
   DWORD                 length,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametreler
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
