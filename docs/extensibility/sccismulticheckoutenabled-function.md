---
title: Sccımulticheckoutenabled Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd8fb5439ac68200ba1a3bbf3af665595528173e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721076"
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
 IDE, dosyaların birden fazla kullanıcı tarafından aynı anda kullanıma alınmış olup olmadığını belirlemede iki denetim yapar. İlk olarak, kaynak denetim sisteminin birden çok kullanıma almayı desteklemesi gerekir. Kaynak denetimi eklentisi, `SCC_CAP_MULTICHECKOUT` belirterek başlatma sırasında bu özelliği belirtebilir. Daha sonra ikinci bir denetim olarak, IDE, geçerli projenin birden çok kullanıma almayı destekleyip desteklemediğini öğrenmek için bu işlevi çağırır. Seçili proje için çoklu kullanıma alma işlemleri destekleniyorsa, eklenti bir başarı kodu döndürür ve `pbMultiCheckout` sıfır olmayan (`TRUE`) veya `FALSE` olarak ayarlar.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)