---
title: Sccımulticheckoutenabled Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 009bc5ba0bb307d0aaee78076266260aa5bb20ef
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924816"
---
# <a name="sccismulticheckoutenabled-function"></a>SccIsMultiCheckoutEnabled İşlevi
Bu işlev, kaynak denetimi eklentisinin bir dosyada birden çok kullanıma almayı izin verip içermediğini denetler.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccIsMultiCheckoutEnabled(
   LPVOID pContext,
   LPBOOL pbMultiCheckout
);
```

#### <a name="parameters"></a>Parametreler
 pContext

'ndaki Kaynak denetimi eklentisi bağlam yapısı.

 pbMultiCheckout

dışı Bu proje için çoklu kullanıma alma işlemleri yapılıp yapılmayacağını belirtir (sıfır dışında çoklu kullanıma alma işlemleri desteklenir).

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Denetim başarılı oldu.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Özel olmayan hata.|

## <a name="remarks"></a>Açıklamalar
 IDE, dosyaların birden fazla kullanıcı tarafından aynı anda kullanıma alınmış olup olmadığını belirlemede iki denetim yapar. İlk olarak, kaynak denetim sisteminin birden çok kullanıma almayı desteklemesi gerekir. Kaynak denetimi eklentisi, ' i belirterek başlatma sırasında bu özelliği belirtebilir `SCC_CAP_MULTICHECKOUT` . Daha sonra ikinci bir denetim olarak, IDE, geçerli projenin birden çok kullanıma almayı destekleyip desteklemediğini öğrenmek için bu işlevi çağırır. Seçili proje için birden fazla kullanıma alma destekleniyorsa, eklenti bir başarı kodu döndürür ve `pbMultiCheckout` sıfır olmayan ( `TRUE` ) veya olarak ayarlar `FALSE` .

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
