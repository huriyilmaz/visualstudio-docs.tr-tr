---
description: İşlevin yığın çerçevesi çalışma zamanı hata denetimi ile derlendiğini bildiren bir değer alır. Bu,/RTCs bayrağıdır.
title: 'IDiaSymbol:: get_isRTCs | Microsoft Docs'
ms.date: 04/27/2021
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isRTCs method
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: be3833af7ea6dc26e51ef24077f762b3c2a001bc74459820b56f73e868849099
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121404718"
---
# <a name="idiasymbolget_isrtcs"></a>IDiaSymbol:: get_isRTCs

İşlevin yığın çerçevesi çalışma zamanı hata denetimi ile derlendiğini belirten bir değer döndürür. Bu,/RTCs bayrağıdır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_isRTCs ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler

 `pRetVal`

dışı İşlevin yığın çerçevesi çalışma zamanı hata denetimi ile derlenip derlenmediğini belirten bir BOOL işaretçisi.

## <a name="return-value"></a>Dönüş Değeri

 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, döndürür `S_FALSE` veya hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar

bu yöntem, Visual Studio 2019 sürüm 16,10 Preview 2 ' den itibaren desteklenir.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üst bilgi|dia2. h|
|Sürüm:|DIA SDK v 7.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
