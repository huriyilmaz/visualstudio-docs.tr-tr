---
title: 'IDiaSymbol:: get_restrictedType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c48b00a6-26b0-47b0-b824-fe44dedbc756
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eac7e512d2fbfb5367725b3878d292444961b6de
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739403"
---
# <a name="idiasymbolget_restrictedtype"></a>IDiaSymbol::get_restrictedType
@No__t_0 işaretçisinin kısıtlı olarak işaretlenip işaretlenmediğini belirtir.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_restrictedType(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı @No__t_1 işaretçisinin kısıtlı olarak işaretlenip işaretlenmediğini belirten `BOOL` işaretçisi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, `S_FALSE` veya bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)