---
title: 'IDiaSymbol:: get_numberOfAcceleratorPointerTags | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 1886e3ec-b227-4187-8d93-c5144b4b77ae
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a4690afe754db2c5e82d200de780d28aae3c652e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85462778"
---
# <a name="idiasymbolget_numberofacceleratorpointertags"></a>IDiaSymbol::get_numberOfAcceleratorPointerTags
C++ AMP saplama işlevindeki Hızlandırıcı işaretçisi etiketlerinin sayısını döndürür.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT get_numberOfAcceleratorPointerTags(
   DWORD* count);
```

#### <a name="parameters"></a>Parametreler
 `count`

dışı Bir `DWORD` C++ amp saplama işlevindeki Hızlandırıcı işaretçisi etiketlerinin sayısını tutan bir işaretçisi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, `IDiaSymbol` C++ amp Hızlandırıcı saplama işlevine karşılık gelen bir arabirim üzerinde çağrılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)