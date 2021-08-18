---
title: CvIsEnabled İşlev | Microsoft Docs
description: Eşzamanlılık Görselleştiricisi SDK'sı cvIsEnabled (C kitaplığı) işlevi için başvuru bilgilerine bakın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvIsEnabledEx
- cvmarkers/CvIsEnabled
helpviewer_keywords:
- CvIsEnabled method
- CvIsEnabledEx method
ms.assetid: 2e4fea6d-758d-4150-8744-6102a1d58c1c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 4bb2e5bf40c038456853a06b9b43a9ee03d8e051
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122084525"
---
# <a name="cvisenabled-function"></a>CvIsEnabled işlevi
Herhangi bir oturumun belirtilen ETW sağlayıcısını etkinleştirip etkinleştirmemiş olduğunu belirler.

## <a name="syntax"></a>Sözdizimi

```C
HRESULT CvIsEnabled(
   _In_ PCV_PROVIDER pProvider
);
HRESULT CvIsEnabledEx(
   _In_ PCV_PROVIDER pProvider,
   _In_ CV_IMPORTANCE level,
   _In_ int category
);
```

#### <a name="parameters"></a>Parametreler
 `category` Kategori.

 `level` Önem düzeyi.

 `pProvider` Geçerli sağlayıcı nesnesi. NULL olamaz.

## <a name="return-value"></a>Döndürülen değer
 S_OK etkinse bu soruna neden olabilir. S_FALSE devre dışı bırakılmıştır. Hata varsa hata kodu. Hata koşullarını kontrol etmek için BAŞARILI makroyu kullanın ve ardından S_OK/S_FALSE.

## <a name="requirements"></a>Gereksinimler
 **Üst bilgi:** *cvmarkers.h*

## <a name="see-also"></a>Ayrıca bkz.
- [C++ kitaplık başvurusu](../profiling/cpp-library-reference.md)