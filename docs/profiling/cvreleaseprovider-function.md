---
title: CvReleaseProvider Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvReleaseProvider
helpviewer_keywords:
- CvReleaseProvider method
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0347d3e2345defb13a67e0e0d730e010be618a21
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85332187"
---
# <a name="cvreleaseprovider-function"></a>CvReleaseProvider işlevi
Bırakma işareti sağlayıcısı. İşaretleyici sağlayıcının bırakılması, bu sağlayıcının daha önce oluşturulmuş işaretleyici serisini etkilemez. İşaretleyici serisinin, CvReleaseMarkerSeries çağrısıyla ayrı olarak serbest bırakılması gerekir. Sağlayıcı yayınlanamaması bellek sızıntısına neden olur.

## <a name="syntax"></a>Söz dizimi

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