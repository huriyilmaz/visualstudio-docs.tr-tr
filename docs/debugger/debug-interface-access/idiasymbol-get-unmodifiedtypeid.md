---
title: 'IDiaSymbol:: get_unmodifiedTypeId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 4f7fc73c-f524-4d7a-b378-a9ab99a96104
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 49cf159501e3f582010d514a586151e0626fc8f7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738968"
---
# <a name="idiasymbolget_unmodifiedtypeid"></a>IDiaSymbol::get_unmodifiedTypeId
Özgün (değiştirilmemiş) türün KIMLIĞINI alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_unmodifiedTypeId(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı KIMLIĞI tutan `DWORD` için bir işaretçi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, `S_FALSE` veya bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)