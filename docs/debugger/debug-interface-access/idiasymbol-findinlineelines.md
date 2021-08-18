---
description: Bir istemcinin satır içinde, doğrudan veya dolaylı olarak bu sembolde yer alan tüm işlevlerin satır numarası bilgileri arasında bir numaralandırarak bir numaralandırıcısını verir.
title: IDiaSymbol::findInlineeLines | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 56ba4bc0-8f96-47c2-8b18-332b4e7c2d91
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: df3fcddf2f31282d27e6f9a5744f2cf8592d2a1e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122036306"
---
# <a name="idiasymbolfindinlineelines"></a>IDiaSymbol::findInlineeLines
Bir istemcinin satır içinde, doğrudan veya dolaylı olarak bu sembolde yer alan tüm işlevlerin satır numarası bilgileri arasında bir numaralandırarak bir numaralandırıcısını verir.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findInlineeLines ( 
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametreler
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
