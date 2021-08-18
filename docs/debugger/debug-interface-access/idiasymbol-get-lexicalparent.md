---
description: Sembolün sözcük üst öğesi için bir başvuru verir.
title: IDiaSymbol::get_lexicalParent | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: d4d05b11e2c42ffdc9ab3ea5c3b38ebe7585881f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122066018"
---
# <a name="idiasymbolget_lexicalparent"></a>IDiaSymbol::get_lexicalParent
Sembolün sözcük üst öğesi için bir başvuru verir.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_lexicalParent ( 
   IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] Sembolün sözcük üst öğelerini temsil eden bir [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` hata kodu döndürür.

> [!NOTE]
> dönüş `S_FALSE` değeri, özelliğin sembol için kullanılamaz olduğu anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Bir sembolün sözcük üst öğesi, kapsayan işlev veya modüldür. Örneğin, bir işlev parametresinin veya yerel değişkenin sözcük üst öğesi işlevin kendisiyken işlevin sözcük üst öğesi, içinde tanımlandığı modüldür.

 Sözcük sözcük üstleri olarak görüne olası semboller Sembol Türlerinin [Sözcük Hiyerarşisi'ne belgelenmiş.](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Simge Türlerinin Sözcük Hiyerarşisi](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
