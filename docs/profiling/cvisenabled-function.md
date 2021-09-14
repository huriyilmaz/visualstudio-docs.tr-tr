---
title: CvIsEnabled Işlevi | Microsoft Docs
description: Eşzamanlılık Görselleştiricisi SDK işlevi CvIsEnabled (C Kitaplığı) için başvuru bilgilerine bakın.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627027"
---
# <a name="cvisenabled-function"></a>CvIsEnabled işlevi
Belirtilen ETW sağlayıcısını herhangi bir oturumun etkinleştirilip etkinleştirilmediğini belirler.

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
 `category` Alan.

 `level` Önem düzeyi.

 `pProvider` Geçerli sağlayıcı nesnesi. NULL olamaz.

## <a name="return-value"></a>Döndürülen değer
 Sağlayıcı Şu anda etkin ise S_OK. Sağlayıcı Şu anda devre dışıysa S_FALSE. Herhangi bir hata olması durumunda hata kodu. Hata durumunu denetlemek için başarısız makroyu kullanın ve ardından S_OK/S_FALSE kontrol edin.

## <a name="requirements"></a>Gereksinimler
 **Üst bilgi:** *cvişaretleyiciler. h*

## <a name="see-also"></a>Ayrıca bkz.
- [C++ Kitaplığı başvurusu](../profiling/cpp-library-reference.md)