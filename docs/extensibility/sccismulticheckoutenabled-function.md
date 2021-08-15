---
description: Bu işlev, kaynak denetimi eklentisinin bir dosyada birden çok iadeye izin verip sağlamay olmadığını denetler.
title: SccIsMultiCheckoutEnabled İşlev | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 90efd3f727611492b0afe2269b5464ae303d840efe2472e987a5450022117040
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121237767"
---
# <a name="sccismulticheckoutenabled-function"></a>SccIsMultiCheckoutEnabled İşlevi
Bu işlev, kaynak denetimi eklentisinin bir dosyada birden çok iadeye izin verip sağlamay olmadığını denetler.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccIsMultiCheckoutEnabled(
   LPVOID pContext,
   LPBOOL pbMultiCheckout
);
```

#### <a name="parameters"></a>Parametreler
 Pcontext

[in] Kaynak denetimi eklentisi bağlam yapısı.

 pbMultiCheckout

[out] Bu proje için birden çok iadenin etkinleştirilip etkinleştirilmemiş olduğunu belirtir (sıfır olmayan, birden çok iadenin destekte olduğu anlamına gelir).

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetimi eklentisinin aşağıdaki değerlerden birini geri dönmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Denetim başarılı oldu.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Belirtilmeyen hata.|

## <a name="remarks"></a>Açıklamalar
 IDE, dosyaların birden fazla kullanıcı tarafından aynı anda kullanıma alınmış olup olmadığını belirlemek için iki denetim yapar. İlk olarak, kaynak denetim sisteminin birden çok iadeyi desteklemesi gerekir. Kaynak denetimi eklentisi, başlatma sırasında belirterek bu özelliği `SCC_CAP_MULTICHECKOUT` belirterek. Bundan sonra, ikinci bir denetim olarak IDE, geçerli projenin birden çok iadeyi destekleyip destekleme olmadığını belirlemek için bu işlevi çağırıyor. Seçilen proje için birden çok onay destekleneyse eklenti bir başarı kodu döndürür ve sıfır olmayan ( ) veya `pbMultiCheckout` `TRUE` olarak `FALSE` ayarlar.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
