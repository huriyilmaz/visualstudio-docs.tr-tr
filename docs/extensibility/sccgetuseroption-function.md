---
title: SccGetUserOption Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cd024aa12b263eab7fea4bd80a0e77a3bbad5f1c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721448"
---
# <a name="sccgetuseroption-function"></a>SccGetUserOption İşlevi
Bu işlev, kullanıcıya özgü çeşitli seçenekleri alır.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccGetUserOption(
   LPVOID pContext,
   LONG nOption,
   LPLONG lpVal
);
```

#### <a name="parameters"></a>Parametreler
 pContext

'ndaki Kaynak denetimi eklentisi bağlam işaretçisi.

 nOption

'ndaki Alma seçeneği (olası seçeneklere yönelik açıklamalar bölümüne bakın).

 lpVal

dışı Seçenekle ilişkili değer.

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Seçenek başarıyla alındı.|
|SCC_E_OPNOTSUPPORTED|Seçenek desteklenmiyor.|
|SCC_E_NONSPECIFICERROR|Belirtilmeyen bir hata oluştu.|

## <a name="remarks"></a>Açıklamalar
 Aşağıdaki seçenekler bu komut tarafından desteklenir:

|Kullanıcı seçeneği|Açıklama|
|-----------------|-----------------|
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Kullanıcının dosyaların yerel sürümünü kullanıma almak isteyip istemediğini belirler. `lpVal` `SCC_USEROPT_COLV_YES` atanır (Kullanıcı yerel dosyaları kullanıma almak istiyor) veya `SCC_USEROPT_COLV_NO`.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [Hata Kodları](../extensibility/error-codes.md)