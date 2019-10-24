---
title: 'IDiaSymbol:: get_RValueReference | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_RValueReference method
ms.assetid: c6c8c543-253e-4c23-a939-3e66f3db0ee2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 43ef604b55cd29d7acf86f38d307dff3958d0162
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739414"
---
# <a name="idiasymbolget_rvaluereference"></a>IDiaSymbol::get_RValueReference
İşaretçi türünün bir rvalue başvurusu olup olmadığını belirten bir bayrak alır. [SymTagEnum numaralandırması](../../debugger/debug-interface-access/symtagenum.md) bir işaretçi türüne ayarlandığında kullanın.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_RValueReference (
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı İşaretçi bir rvalue başvurusu ise `TRUE` döndürür; Aksi takdirde, `FALSE` döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, `S_FALSE` veya bir hata kodu döndürür.

> [!NOTE]
> @No__t_0 dönüş değeri özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: dia2. h

 Kitaplık: diaguid. lib

 DLL: msdia100. dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)