---
title: CvReleaseProvider Işlevi | Microsoft Docs
description: CvReleaseProvider (C Kitaplığı) Eşzamanlılık Görselleştiricisi SDK 'Sı işlevine yönelik başvuru bilgilerine bakın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvReleaseProvider
helpviewer_keywords:
- CvReleaseProvider method
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 19dbf0acd7f3522632cce83fee90e18a21a104cf
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625436"
---
# <a name="cvreleaseprovider-function"></a>CvReleaseProvider işlevi
Bırakma işareti sağlayıcısı. İşaretleyici sağlayıcının bırakılması, bu sağlayıcının daha önce oluşturulmuş işaretleyici serisini etkilemez. İşaretleyici serisinin, CvReleaseMarkerSeries çağrısıyla ayrı olarak serbest bırakılması gerekir. Sağlayıcı yayınlanamaması bellek sızıntısına neden olur.

## <a name="syntax"></a>Sözdizimi

```C
HRESULT CvReleaseProvider(
   _In_ PCV_PROVIDER pProvider
);
```

#### <a name="parameters"></a>Parametreler
 `pProvider` Sağlayıcı bağlamı. NULL olamaz.

## <a name="return-value"></a>Dönüş Değeri
 S_OK bir hata olması durumunda sağlayıcı başarıyla yayımlanmışsa veya hata kodu. Hata koşulunu denetlemek için başarılı/başarısız makroları kullanın.

## <a name="requirements"></a>Gereksinimler
 **Üst bilgi:** *cvişaretleyiciler. h*

## <a name="see-also"></a>Ayrıca bkz.
- [C++ Kitaplığı başvurusu](../profiling/cpp-library-reference.md)