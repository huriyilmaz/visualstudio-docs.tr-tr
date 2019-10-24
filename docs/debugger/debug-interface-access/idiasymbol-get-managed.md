---
title: 'IDiaSymbol:: get_managed | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_managed method
ms.assetid: a69d00be-2a89-415c-b116-385c422e2fd5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 515b8931eff37338aa53ac204c7ef61a27987aba
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739809"
---
# <a name="idiasymbolget_managed"></a>IDiaSymbol::get_managed
Simgenin yönetilen koda başvurduğunu belirten bir bayrak alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_managed ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Sembol yönetilen koda başvuruyorsa `TRUE` döndürür; Aksi takdirde, `FALSE` döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, `S_FALSE` veya bir hata kodu döndürür.

> [!NOTE]
> @No__t_0 dönüş değeri özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)