---
description: Bu sembol deposundaki simgelere karşılık gelen yürütülebilir dosyanın yükleme adresini alır.
title: 'IDiaSession:: get_loadAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::get_loadAddress method
ms.assetid: 5162ae1a-38e3-4571-8995-4ed9be1dec3e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 1ab5aee87bb562ccb4bd373999d2e30ab5565e36
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122058922"
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

dışı Bir .exe dosyası veya .dll dosyasının yüklendiği bir sanal adres (VA) döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Açıkça [IDiaSession::p ut_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) yöntemi kullanılarak ayarlanmamışsa döndürülen yükleme adresi her zaman sıfırdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)
