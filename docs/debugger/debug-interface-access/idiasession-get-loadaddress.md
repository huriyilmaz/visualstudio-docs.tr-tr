---
title: 'IDiaSession:: get_loadAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::get_loadAddress method
ms.assetid: 5162ae1a-38e3-4571-8995-4ed9be1dec3e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b23aff5cd5d2b94a44e3e9139ff4c97acb2225d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741937"
---
# <a name="idiasessionget_loadaddress"></a>IDiaSession::get_loadAddress
Bu sembol deposundaki simgelere karşılık gelen yürütülebilir dosyanın yükleme adresini alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_loadAddress ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Bir. exe dosyasının veya. dll dosyasının yüklendiği bir sanal adres (VA) döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Açıkça [IDiaSession::P ut_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) yöntemi kullanılarak ayarlanmamışsa döndürülen yükleme adresi her zaman sıfırdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)