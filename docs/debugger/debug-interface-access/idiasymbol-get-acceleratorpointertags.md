---
description: Bir C++ AMP hızlandırıcı saplama işlevine karşılık gelen tüm hızlandırıcı işaretçisi etiket değerlerini döndürür.
title: IDiaSymbol::get_acceleratorPointerTags | Microsoft Docs
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
ms.openlocfilehash: 3bd2de4fe6599ec9dfc7d732a83dd4f88e04fabb
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628923"
---
# <a name="idiasymbolget_acceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
Bir C++ AMP hızlandırıcı saplama işlevine karşılık gelen tüm hızlandırıcı işaretçisi etiket değerlerini döndürür.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_acceleratorPointerTags(
   DWORD          cnt,
   DWORD*         pcnt,
   DWORD*         pPointerTags);
```

#### <a name="parameters"></a>Parametreler
 `cnt`

[in] Çıkış dizisinin `pPointerTags` boyutu.

 `pcnt`

[out] C++ AMP hızlandırıcı saplama işlevinde hızlandırıcı işaretçisi etiketlerinin sayısı.

 `pPointerTags`

[out] Hızlandırıcı `DWORD` saplama işlevinde hızlandırıcı işaretçisi etiket değerleriyle doldurulmuş C++ AMP işaretçisi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, bir C++ AMP `IDiaSymbol` hızlandırıcı saplama işlevine karşılık gelen bir arabirimde çağrılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
