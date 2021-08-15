---
description: Her işleve eklenen fazladan panelin boyutunu alın.
title: IDiaSymbol::get_framePadSize | Microsoft Docs
ms.date: 04/27/2021
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_framePadSize method
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 72f9920d5c2a690f9b2687c14b60ae298c4fde4feb009675d157e7158cdd5e30
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121240547"
---
# <a name="idiasymbolget_framepadsize"></a>IDiaSymbol::get_framePadSize

Her işleve eklenen fazladan panelin boyutunu alın.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_framePadSize ( 
   DWORD* pPadSize
);
```

#### <a name="parameters"></a>Parametreler

 `pPadSize`

[out] Her işleve eklenen ek paneli boyutunu döndürür.

## <a name="return-value"></a>Dönüş Değeri

 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` hata kodu döndürür.

> [!NOTE]
> dönüş `S_FALSE` değeri, özelliğin sembol için kullanılamaz olduğu anlamına gelir.

## <a name="remarks"></a>Açıklamalar

Ek panelin boyutu genellikle Düzenle ve Devam Tarafından kullanılır.

Bu yöntem, 2019 Visual Studio 16.10 Önizleme 2 sürümünden itibaren de destekleni.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üstbilgi:|dia2.h|
|Sürüm:|DIA SDK v7.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
