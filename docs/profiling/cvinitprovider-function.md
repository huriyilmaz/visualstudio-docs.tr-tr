---
title: CvInitProvider Işlevi | Microsoft Docs
description: CvInitProvider (C Kitaplığı) Eşzamanlılık Görselleştiricisi SDK 'Sı işlevine yönelik başvuru bilgilerine bakın.
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
ms.workload:
- multiple
ms.openlocfilehash: f23d3ceadf2ee8d1a0c6b53b395c379caf505179
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941001"
---
# <a name="cvinitprovider-function"></a>CvInitProvider işlevi
İşaretleyici sağlayıcısını başlatır. Diğer Eşzamanlılık Görselleştiricisi SDK işlevlerinden önce çağrılmalıdır.

## <a name="syntax"></a>Sözdizimi

```C
HRESULT CvInitProvider(
   _In_ const GUID* pGuid,
   _Out_ PCV_PROVIDER* ppProvider
);
```

#### <a name="parameters"></a>Parametreler
 `pGuid` Sağlayıcı GUID 'i. NULL olamaz.

 `ppProvider` Sağlayıcı bağlamını depolayacak bir çıktı değişkeninin adresi. NULL olamaz.

## <a name="return-value"></a>Döndürülen değer
 Sağlayıcı başarıyla başlatıldığında S_OK veya herhangi bir hata olması durumunda hata kodu. Hata koşulunu denetlemek için başarılı/başarısız makroları kullanın.

## <a name="requirements"></a>Gereksinimler
 **Üst bilgi:** *cvişaretleyiciler. h*

## <a name="see-also"></a>Ayrıca bkz.
- [C++ Kitaplığı başvurusu](../profiling/cpp-library-reference.md)