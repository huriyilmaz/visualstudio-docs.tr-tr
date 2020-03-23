---
title: CvInitSağlayıcı Fonksiyonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvInitProvider
helpviewer_keywords:
- CvInitProvider method
ms.assetid: ba1863ad-e35f-4d34-a2f2-5e68957d1915
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a97be63cd782397e984fd8dbce7da844efa07540
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62552673"
---
# <a name="cvinitprovider-function"></a>CvInitProvider fonksiyonu
İşaretleyici sağlayıcısını başharfe adamaktadır. Diğer Eşzamanlı Görselleştirici SDK işlevleriönce çağrılmalıdır.

## <a name="syntax"></a>Sözdizimi

```C
HRESULT CvInitProvider(
   _In_ const GUID* pGuid,
   _Out_ PCV_PROVIDER* ppProvider
);
```

#### <a name="parameters"></a>Parametreler
 `pGuid`Sağlayıcı guid. NULL olamaz.

 `ppProvider`Sağlayıcı bağlamını depolayacak bir çıktı değişkeninin adresi. NULL olamaz.

## <a name="return-value"></a>Döndürülen değer
 S_OK sağlayıcı başarıyla başlatılması veya herhangi bir hata olması durumunda hata kodu. Hata durumunu denetlemek için BAŞARILI/BAŞARILI makroları kullanın.

## <a name="requirements"></a>Gereksinimler
 **Üstbilgi:** *cvmarkers.h*

## <a name="see-also"></a>Ayrıca bkz.
- [C++ kitaplık başvurusu](../profiling/cpp-library-reference.md)