---
title: CvInitProvider İşlev | Microsoft Docs
description: Eşzamanlılık Görselleştiricisi SDK'sı işlevi CvInitProvider (C kitaplığı) için başvuru bilgilerine bakın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvInitProvider
helpviewer_keywords:
- CvInitProvider method
ms.assetid: ba1863ad-e35f-4d34-a2f2-5e68957d1915
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c0432a57deee0b88cd0b30d16cc741b391250b55
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627032"
---
# <a name="cvinitprovider-function"></a>CvInitProvider işlevi
İşaretleyici sağlayıcısını başlatılır. Diğer Eşzamanlılık GörselleştiriciSI SDK'sı işlevleri öncesinde çağrılları gerekir.

## <a name="syntax"></a>Sözdizimi

```C
HRESULT CvInitProvider(
   _In_ const GUID* pGuid,
   _Out_ PCV_PROVIDER* ppProvider
);
```

#### <a name="parameters"></a>Parametreler
 `pGuid` Sağlayıcı guid'si. NULL olamaz.

 `ppProvider` Sağlayıcı bağlamını depolar bir çıkış değişkeninin adresi. NULL olamaz.

## <a name="return-value"></a>Döndürülen değer
 S_OK başarıyla başlatılmışsa veya herhangi bir hata olması durumunda hata kodu. Hata koşullarını kontrol etmek için BAŞARILI/BAŞARILI makroları kullanın.

## <a name="requirements"></a>Gereksinimler
 **Üst bilgi:** *cvmarkers.h*

## <a name="see-also"></a>Ayrıca bkz.
- [C++ kitaplık başvurusu](../profiling/cpp-library-reference.md)