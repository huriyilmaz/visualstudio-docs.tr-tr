---
title: SccIsMultiCheckoutEtkin Fonksiyon | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e91eb566a820f4fe11ceb629643e1815dcb87a8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700579"
---
# <a name="sccismulticheckoutenabled-function"></a>SccIsMultiCheckoutEnabled İşlevi
Bu işlev, kaynak denetimi eklentisinin bir dosyada birden çok kullanıma izin verip vermediğini denetler.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccIsMultiCheckoutEnabled(
   LPVOID pContext,
   LPBOOL pbMultiCheckout
);
```

#### <a name="parameters"></a>Parametreler
 Pcontext

[içinde] Kaynak denetimi eklentisi bağlam yapısı.

 pbMultiCheckout

[çıkış] Bu proje için birden çok ödemenin etkin olup olmadığını belirtir (sıfır olmayan, birden çok ödemenin desteklenmediği anlamına gelir).

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetim eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Çek başarılı oldu.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nonspesifik bir hata.|

## <a name="remarks"></a>Açıklamalar
 IDE, dosyaların birden fazla kullanıcı tarafından aynı anda kullanıma alınıp alınamayacağına karar vermek için iki denetim yapar. İlk olarak, kaynak denetim sistemi birden çok ödeme desteği gerekir. Kaynak denetim eklentisi, `SCC_CAP_MULTICHECKOUT`'yi belirterek, başlatma sırasında bu özelliği belirtebilir. Bundan sonra, ikinci bir denetim olarak, IDE geçerli projenin birden çok ödemeyi destekleyip desteklemediğini belirlemek için bu işlevi çağırır. Seçili proje için birden çok ödeme desteklenirse, eklenti bir `pbMultiCheckout` başarı kodu`TRUE`döndürür ve sıfırsız ( ) veya `FALSE`.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
