---
description: C++ AMP hızlandırıcı saplama işlevine karşılık gelen tüm hızlandırıcı işaretçisi etiketi değerlerini döndürür.
title: 'IDiaSymbol:: get_acceleratorPointerTags | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 2620b47cdf732ea849d4e644e1fa621363c77a9ce4cfb77f0f97104c3233a710
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121379985"
---
# <a name="idiasymbolget_acceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
C++ AMP hızlandırıcı saplama işlevine karşılık gelen tüm hızlandırıcı işaretçisi etiketi değerlerini döndürür.

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

dışı C++ AMP hızlandırıcı saplama işlevindeki hızlandırıcı işaretçisi etiketlerinin sayısı.

 `pPointerTags`

dışı `DWORD`C++ AMP hızlandırıcı saplama işlevindeki hızlandırıcı işaretçisi etiket değerleriyle doldurulmuş bir dizi işaretçisi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 bu yöntem, `IDiaSymbol` C++ AMP hızlandırıcı saplama işlevine karşılık gelen bir arabirim üzerinde çağrılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
