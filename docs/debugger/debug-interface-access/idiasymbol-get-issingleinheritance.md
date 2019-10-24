---
title: 'IDiaSymbol:: get_isSingleInheritance | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 46cde656-059b-4c20-9476-3ca68ccc9912
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 96a8ce072fc57dc236dd2025b8ea3c9c5a4b9b79
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740065"
---
# <a name="idiasymbolget_issingleinheritance"></a>IDiaSymbol::get_isSingleInheritance
@No__t_0 işaretçisinin tek devralma ile veri üyesine işaret ettiğini belirtir.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_isSingleInheritance(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı @No__t_1 işaretçisinin tek devralma ile bir veri üyesine işaret ettiğini belirten `BOOL` işaretçisi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, `S_FALSE` veya bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)