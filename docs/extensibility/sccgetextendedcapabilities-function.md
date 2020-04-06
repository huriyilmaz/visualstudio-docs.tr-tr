---
title: SccGetExtendedYetenekleri Fonksiyonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5247f2de7ffc63db7235f915c72b3274b8fee5f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700732"
---
# <a name="sccgetextendedcapabilities-function"></a>SccGetExtendedCapabilities fonksiyonu
Bu işlev, kaynak denetim eklentisi tarafından desteklenen ek özellikler sağlar.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccGetExtendedCapabilities(
   LPVOID pContext,
   LONG lSccExCaps,
   LPBOOL pbSupported
);
```

### <a name="parameters"></a>Parametreler
 Pcontext

[içinde] Kaynak denetimi eklentibağlam işaretçisi.

 lSccExCaps

[içinde] Sınamak için genişletilmiş bir kapasite belirten bir bayrak (olası bayraklar için [Yetenek bayraklarında](../extensibility/capability-flags.md) Genişletilmiş Yetenek Kodu tablosuna bakın).

 pbDesteklenen

[çıkış] Belirtilen yetenek desteklenirse sıfır olmayan (`TRUE`) döndürür; aksi takdirde,`FALSE`sıfır () döndürür.

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetim eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Alabilme yeteneği işlemi başarıyla tamamlandı.|
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Bilinmeyen veya belirtilmeyen hata oluştu.|

## <a name="remarks"></a>Açıklamalar
 Bu yöntem isteğe bağlı olarak çağrılır; diğer bir özellik sınanması gerektiğinde, bu yeteneğin desteklenip desteklenmediğini belirlemek için bu yöntem çağrılır. Aynı anda yalnızca bir bayrak belirtilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak kontrol eklentisi API fonksiyonları](../extensibility/source-control-plug-in-api-functions.md)
- [Hata kodları](../extensibility/error-codes.md)
- [Yetenek bayrakları](../extensibility/capability-flags.md)
