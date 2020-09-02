---
title: 'IDiaSymbol:: get_addressSection | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressSection method
ms.assetid: fe80d479-3bb5-4f55-9b62-1bd58d0a60ce
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2d5f06658cb6d2faad13112813731208075460cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85464361"
---
# <a name="idiasymbolget_addresssection"></a>IDiaSymbol::get_addressSection
Bir adres konumunun bölüm kısmını alır. [LocationType numaralandırması](../../debugger/debug-interface-access/locationtype.md) olarak ayarlandığında kullanın `LocIsStatic` .

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT get_addressSection ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Adres konumunun bölüm bölümünü döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin simge için kullanılamadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Dış DLL 'de bulunan statik üyeler için, bu yöntemin döndürdüğü bölüm 0 olabilir. Bu yöntem üyenin sanal adresini elde etmeye bağlıdır. Sanal adresler yalnızca [IDiaSession](../../debugger/debug-interface-access/idiasession.md) arabirimindeki [IDiaSession::P ut_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) yöntemi dll 'nin yükleme adresini belirten sıfır olmayan bir parametreyle çağrılırsa geçerlidir.

 Bir adresin konum kısmını almak için [IDiaSymbol:: get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md) yöntemini çağırın.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Description|
|-----------------|-----------------|
|Üst bilgi|dia2. h|
|Sürüm:|DIA SDK v 7.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType Numaralandırması](../../debugger/debug-interface-access/locationtype.md)