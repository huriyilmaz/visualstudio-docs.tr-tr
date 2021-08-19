---
description: Sembollerin yükleniyor olduğu dosyanın adını alın.
title: IDiaSymbol::get_symbolsFileName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_symbolsFileName method
ms.assetid: c1aa39ee-d645-431e-bf5f-0640c0998934
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: d151c1ca21b1407f6edcacd7cc2bc3a7d44185c2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147105"
---
# <a name="idiasymbolget_symbolsfilename"></a>IDiaSymbol::get_symbolsFileName
Sembollerin yükleniyor olduğu dosyanın adını alın.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_symbolsFileName ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] Sembollerin yükleniyor olduğu dosyanın adını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> dönüş `S_FALSE` değeri, özelliğin sembol için kullanılamaz olduğu anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Bu özellik yalnızca [SymTagEnum Numaralama](../../debugger/debug-interface-access/symtagenum.md) değeri genel kapsamı olan `SymTagExe` semboller için geçerlidir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum Numaralandırması](../../debugger/debug-interface-access/symtagenum.md)
