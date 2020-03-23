---
title: CvReleaseProvider Fonksiyonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 0008b7476290558c098b2241fde5c9b209933a0a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62974052"
---
# <a name="cvreleaseprovider-function"></a>CvReleaseProvider fonksiyonu
İşaretleyici sağlayıcısını serbest bırakır. İşaretleyici sağlayıcısının serbest bırakılması, bu sağlayıcının daha önce oluşturulmuş işaretçi serisini etkilemez. Marker serisi CvReleaseMarkerSeries çağrısı ile ayrı olarak serbest bırakılmalıdır. Sağlayıcının serbest bırakılamaması bellek sızıntısına neden olur.

## <a name="syntax"></a>Sözdizimi

```C
HRESULT CvReleaseProvider(
   _In_ PCV_PROVIDER pProvider
);
```

#### <a name="parameters"></a>Parametreler
 `pProvider`Sağlayıcı bağlamı. NULL olamaz.

## <a name="return-value"></a>Dönüş Değeri
 Sağlayıcı başarıyla serbest bırakıldığında veya herhangi bir hata olması durumunda hata kodu S_OK. Hata durumunu denetlemek için BAŞARILI/BAŞARILI makroları kullanın.

## <a name="requirements"></a>Gereksinimler
 **Üstbilgi:** *cvmarkers.h*

## <a name="see-also"></a>Ayrıca bkz.
- [C++ kitaplık başvurusu](../profiling/cpp-library-reference.md)