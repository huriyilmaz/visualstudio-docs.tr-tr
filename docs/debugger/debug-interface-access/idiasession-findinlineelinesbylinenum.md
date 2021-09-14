---
description: Bir istemcinin, belirtilen kaynak dosya ve satır numarasında satır içine alınan, doğrudan veya dolaylı olarak tüm işlevlerin satır numarası bilgisinde bir numaralandırarak bir numaralandırır.
title: IDiaSession::findInlineeLinesByLinenum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: cf32ae7c-a0c8-4800-bc8f-d64fdd15fb06
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 4d1260c11aa8e737f9188b86de44cd8e6fdf33cb
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629247"
---
# <a name="idiasessionfindinlineelinesbylinenum"></a>IDiaSession::findInlineeLinesByLinenum
Bir istemcinin, belirtilen kaynak dosya ve satır numarasında satır içine alınan, doğrudan veya dolaylı olarak tüm işlevlerin satır numarası bilgisinde bir numaralandırarak bir numaralandırır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findInlineeLinesByVA ( 
   IDiaSymbol*           compiland,
   IDiaSourceFile*       file,
   DWORD                 linenum,
   DWORD                 column,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametreler
 `compiland`

[in] Satır numaralarının aranacak derlemeyi temsil eden bir [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesnesi. Bu parametre `NULL` olamaz.

 `file`

[in] Arama yapılan kaynak dosyayı temsil eden bir [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) nesnesi. Bu parametre `NULL` olamaz.

 `linenum`

[in] Tek tabanlı bir satır numarası belirtir.

> [!NOTE]
> Tüm satırları belirtmek için sıfır kullanılamaz (tüm satırları bulmak için [IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md) yöntemini kullanın).

 `column`

[in] Sütun numarasını belirtir. Tüm sütunları belirtmek için sıfır kullanın. Sütun, satıra bir bayt kaydırma değeridir.

 `ppResult`

[out] Alınan satır numaralarının listesini içeren bir [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum Numaralandırması](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
