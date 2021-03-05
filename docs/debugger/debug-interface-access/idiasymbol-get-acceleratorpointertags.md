---
description: C++ AMP Hızlandırıcı saplama işlevine karşılık gelen tüm Hızlandırıcı işaretçisi etiketi değerlerini döndürür.
title: 'IDiaSymbol:: get_acceleratorPointerTags | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 99bf6f90cb15484613a6572952a6f8501fa6bf31
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156603"
---
# <a name="idiasymbolget_acceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
C++ AMP Hızlandırıcı saplama işlevine karşılık gelen tüm Hızlandırıcı işaretçisi etiketi değerlerini döndürür.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_acceleratorPointerTags(
   DWORD          cnt,
   DWORD*         pcnt,
   DWORD*         pPointerTags);
```

#### <a name="parameters"></a>Parametreler
 `cnt`

'ndaki Çıktı dizisinin boyutu `pPointerTags` .

 `pcnt`

dışı C++ AMP Hızlandırıcı saplama işlevindeki Hızlandırıcı işaretçisi etiketlerinin sayısı.

 `pPointerTags`

dışı `DWORD` C++ amp Hızlandırıcı saplama işlevindeki Hızlandırıcı işaretçisi etiket değerleriyle doldurulmuş bir dizi işaretçisi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, `IDiaSymbol` C++ amp Hızlandırıcı saplama işlevine karşılık gelen bir arabirim üzerinde çağrılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
