---
title: 'IDiaSymbol:: get_addressOffset | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressOffset method
ms.assetid: c15639b0-7f37-46c7-891b-40273b7f6319
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e5d5c865ca503890f3f29df44bcd65dd10343bf1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99854600"
---
# <a name="idiasymbolget_addressoffset"></a>IDiaSymbol::get_addressOffset
Bir adres konumunun konum kısmını alır. [LocationType numaralandırması](../../debugger/debug-interface-access/locationtype.md) olarak ayarlandığında kullanın `LocIsStatic` .

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_addressOffset ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Bir adres konumunun konum parçasını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin simge için kullanılamadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Dış DLL 'de bulunan statik üyeler için, bu yöntemin döndürdüğü fark 0 olabilir. Bu yöntem üyenin sanal adresini elde etmeye bağlıdır. Sanal adresler yalnızca [IDiaSession](../../debugger/debug-interface-access/idiasession.md) arabirimindeki [IDiaSession::P ut_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) yöntemi dll 'nin yükleme adresini belirten sıfır olmayan bir parametreyle çağrılırsa geçerlidir.

 Bir adresin bölüm bölümünü almak için [IDiaSymbol:: get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md) yöntemini çağırın.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üst bilgi|dia2. h|
|Sürüm:|DIA SDK v 7.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType Numaralandırması](../../debugger/debug-interface-access/locationtype.md)
- [IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)
- [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)