---
title: CvWriteMessage İşlevi | Microsoft Docs
description: Eşzamanlılık Görselleştiricisi SDK'sı işlevi CvWriteMessage (C kitaplığı) için başvuru bilgilerine bakın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvWriteMessageW
- cvmarkers/CvWriteMessageExW
- cvmarkers/CvWriteMessageVA
- cvmarkers/CvWriteMessageExVW
- cvmarkers/CvWriteMessageExA
- cvmarkers/CvWriteMessageA
- cvmarkers/CvWriteMessageExVA
- cvmarkers/CvWriteMessageVW
helpviewer_keywords:
- CvWriteMessageExVA method
- CvWriteMessageW method
- CvWriteMessageVW method
- CvWriteMessageExVW method
- CvWriteMessageExW method
- CvWriteMessageA method
- CvWriteMessageVA method
- CvWriteMessageExA method
ms.assetid: e20ae7be-bfa7-437a-b8c1-fa0f1baa7f83
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 67e6b88c34520f805bffb7af5d12465d4f2ee427
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627015"
---
# <a name="cvwritemessage-function"></a>CvWriteMessage işlevi
Eşzamanlılık Görselleştiricisi izleme dosyasına bir ileti yazar.

## <a name="syntax"></a>Sözdizimi

```C
HRESULT CvWriteMessageW(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ PCWSTR pMessage,
    ...
    );

HRESULT CvWriteMessageA(
    PCV_MARKERSERIES pMarkerSeries,
    _In_ PCSTR pMessage,
    ...
    );

HRESULT CvWriteMessageVW(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ PCWSTR pMessage,
    _In_ va_list argList);

HRESULT CvWriteMessageVA(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ PCSTR pMessage,
    _In_ va_list argList);

HRESULT CvWriteMessageExW(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ CV_IMPORTANCE level,
    _In_ int category,
    _In_ PCWSTR pMessage,
    ...
    );

HRESULT CvWriteMessageExA(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ CV_IMPORTANCE level,
    _In_ int category,
    _In_ PCSTR pMessage,
    ...
    );

HRESULT CvWriteMessageExVW(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ CV_IMPORTANCE level,
    _In_ int category,
    _In_ PCWSTR pMessage,
    _In_ va_list argList);

HRESULT CvWriteMessageExVA(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ CV_IMPORTANCE level,
    _In_ int category,
    _In_ PCSTR pMessage,
    _In_ va_list argList);
```

#### <a name="parameters"></a>Parametreler
 `argList` Bağımsız değişkenlerin listesi.

 `category` Aralığın kategorisi

 `level` Aralığın önem düzeyi.

 `pMarkerSeries` Geçerli işaretçi serisi bağlamı. NULL olamaz.

 `pMessage` İleti biçimi dizesi. NULL olamaz.

## <a name="return-value"></a>Döndürülen değer
 S_OK başarıyla yazıldığı zaman iletiyi görüntüler. Hata varsa hata kodu. Hata koşullarını kontrol etmek için BAŞARILI/BAŞARILI makroları kullanın.

## <a name="requirements"></a>Gereksinimler
 **Üst bilgi:** *cvmarkers.h*

 **Unicode:** CvWriteMessageW, CvWriteMessageVW, CvWriteMessageExW, CvWriteMessageExVW

 **ANSI:** CvWriteMessageA, CvWriteMessageVA, CvWriteMessageExA, CvWriteMessageExVA

## <a name="see-also"></a>Ayrıca bkz.
- [C++ kitaplık başvurusu](../profiling/cpp-library-reference.md)