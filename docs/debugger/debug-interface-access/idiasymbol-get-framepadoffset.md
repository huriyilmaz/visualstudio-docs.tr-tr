---
description: Çerçeve işaretçisi kaydındaki yığın panelinin konumunu alır.
title: 'IDiaSymbol:: get_framePadOffset | Microsoft Docs'
ms.date: 04/27/2021
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_framePadOffset method
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 455e617188a58090f3bd6229ab008847912b1f19
ms.sourcegitcommit: 30c404655fb83ea28f96ab1edb1c09b4d8d7eec4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2021
ms.locfileid: "108217252"
---
# <a name="idiasymbolget_framepadoffset"></a>IDiaSymbol:: get_framePadOffset

Çerçeve işaretçisi kaydındaki yığın panelinin konumunu alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_framePadOffset ( 
   DWORD* pPadOffset
);
```

#### <a name="parameters"></a>Parametreler

 `pPadOffset`

dışı Yığın panelinin sapmasını döndürür.

## <a name="return-value"></a>Dönüş Değeri

 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, döndürür `S_FALSE` veya hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar

Bu yöntem, Visual Studio 2019 sürüm 16,10 Preview 2 ' den itibaren desteklenir.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üst bilgi|dia2. h|
|Sürüm:|DIA SDK v 7.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
