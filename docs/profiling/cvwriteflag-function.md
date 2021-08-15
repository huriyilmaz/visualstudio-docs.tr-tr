---
title: CvWriteFlag İşlev | Microsoft Docs
description: Eşzamanlılık Görselleştiricisi SDK'sı işlevi CvWriteFlag (C kitaplığı) için başvuru bilgilerine bakın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvWriteFlagExVA
- cvmarkers/CvWriteFlagExW
- cvmarkers/CvWriteFlagExVW
- cvmarkers/CvWriteFlagExA
helpviewer_keywords:
- CvWriteFlagExW method
- CvWriteFlagExVA method
- CvWriteFlagExA method
- CvWriteFlagExVW method
ms.assetid: ee9da1e2-7b34-4cba-81e2-215d25d32e4d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: bfc1d43526eddfc20e0ec639559be9bc75370e19692fde8496a227ac3c9b4538
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121301557"
---
# <a name="cvwriteflag-function"></a>CvWriteFlag işlevi
Eşzamanlılık Görselleştiricisi izleme dosyasına bir bayrak yazar.

## <a name="syntax"></a>Sözdizimi

```C
HRESULT CvWriteFlagExW(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ CV_IMPORTANCE level,
    _In_ int category,
    _In_ PCWSTR pMessage,
    ...
    );

HRESULT CvWriteFlagExA(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ CV_IMPORTANCE level,
    _In_ int category,
    _In_ PCSTR pMessage,
    ...
    );

HRESULT CvWriteFlagExVW(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ CV_IMPORTANCE level,
    _In_ int category,
    _In_ PCWSTR pMessage,
    _In_ va_list argList);

HRESULT CvWriteFlagExVA(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ CV_IMPORTANCE level,
    _In_ int category,
    _In_ PCSTR pMessage,
    _In_ va_list argList);
```

#### <a name="parameters"></a>Parametreler
 `argList` Bağımsız değişkenlerin listesi.

 `category` Kategori.

 `level` Önem düzeyi.

 `pMarkerSeries` Geçerli işaretçi serisi bağlamı. NULL olamaz.

 `pMessage` İleti biçimi dizesi. NULL olamaz.

## <a name="return-value"></a>Döndürülen değer
 S_OK başarıyla yazıldığı zaman iletiyi görüntüler. Hata varsa hata kodu. Hata koşullarını kontrol etmek için BAŞARILI/BAŞARILI makroları kullanın.

## <a name="requirements"></a>Gereksinimler
 **Üst bilgi:** *cvmarkers.h*

 **Unicode:** CvWriteFlagExW, CvWriteFlagExVW

 <strong>ANSI:</strong> CvWriteFlagExA, CvWriteFlagExVA

## <a name="see-also"></a>Ayrıca bkz.
- [C++ kitaplık başvurusu](../profiling/cpp-library-reference.md)