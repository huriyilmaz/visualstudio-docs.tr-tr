---
title: 'IDiaSymbol:: get_lexicalParent | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_lexicalParent method
ms.assetid: 4d119965-33a8-474c-9c64-95c5218c389c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: afac75a650f3ffc8dc365626a7a61fea8c3193f4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853956"
---
# <a name="idiasymbolget_lexicalparent"></a>IDiaSymbol::get_lexicalParent
Simgenin sözcük üst öğesi için bir başvuru alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_lexicalParent ( 
   IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Simgenin sözcük üst öğesini temsil eden bir [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, döndürür `S_FALSE` veya hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Bir simgenin sözcük üst öğesi kapsayan işlev veya modüldür. Örneğin, işlev parametresinin veya yerel değişkenin sözlü üst öğesi işlevin kendisidir, çünkü işlevin alt öğe üst öğesi içinde tanımlandığı modüldür.

 Sözcük üst öğeleri olarak görünebilen olası semboller, [sembol türlerinin sözlü hiyerarşisinde](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)belgelenmiştir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Simge Türlerinin Sözcük Hiyerarşisi](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)