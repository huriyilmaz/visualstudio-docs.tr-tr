---
title: SccGetUserOption Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7e4bc3e4bf6acef8ff8de1cdcecb2596dcf6d86e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844560"
---
# <a name="sccgetuseroption-function"></a>SccGetUserOption İşlevi
Bu işlev, kullanıcıya özgü çeşitli seçenekleri alır.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccGetUserOption(
   LPVOID pContext,
   LONG nOption,
   LPLONG lpVal
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

|Kullanıcı seçeneği|Description|
|-----------------|-----------------|
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Kullanıcının dosyaların yerel sürümünü kullanıma almak isteyip istemediğini belirler. `lpVal` atandı `SCC_USEROPT_COLV_YES` (Kullanıcı yerel dosyaları kullanıma almak istiyor) veya `SCC_USEROPT_COLV_NO` .|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [Hata Kodları](../extensibility/error-codes.md)
