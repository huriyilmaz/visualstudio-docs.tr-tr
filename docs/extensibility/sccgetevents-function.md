---
title: SccGetEvents Fonksiyonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 91b3debf0e686ceece3048cf3d92b629e3359edd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700814"
---
# <a name="sccgetevents-function"></a>SccGetEvents fonksiyonu
Bu işlev sıralanmış durum olayını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccGetEvents (
   LPVOID pvContext,
   LPSTR  lpFileName,
   LPLONG lpStatus,
   LPLONG pnEventsRemaining
);
```

### <a name="parameters"></a>Parametreler
 pvContext

[içinde] Kaynak denetimi eklentisi bağlam yapısı.

 lpFileName

[içinde, dışarı] Kaynak denetim eklentisinin döndürülen dosya adını (_MAX_PATH karaktere kadar) koyduğu arabellek.

 lpDurum

[içinde, dışarı] Durum kodunu döndürür (olası değerler için [Dosya durum koduna](../extensibility/file-status-code-enumerator.md) bakın).

 pnEtkinliklerKalan

[içinde, dışarı] Bu aramadan sonra kuyrukta kalan giriş sayısını döndürür. Bu numara büyükse, arayan kişi tüm bilgileri aynı anda almak için [SccQueryInfo'yu](../extensibility/sccqueryinfo-function.md) aramaya karar verebilir.

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetim eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Olayların başarılı ol.|
|SCC_E_OPNOTSUPPORTED|Bu işlev desteklenmez.|
|SCC_E_NONSPECIFICERROR|Nonspesifik bir hata.|

## <a name="remarks"></a>Açıklamalar
 Bu işlev, kaynak denetimi altındaki dosyalar için durum güncelleştirmeleri olup olmadığını görmek için boşta işleme sırasında çağrılır. Kaynak denetimi eklentisi bildiği tüm dosyaların durumunu korur ve durum değişikliği eklentitarafından ne zaman belirtilirse, durum ve ilişkili dosya bir sırada depolanır. Çağrıldığında, `SccGetEvents` sıranın üst öğesi alınır ve döndürülür. Bu işlev yalnızca önceden önbelleğe alınmış bilgileri döndürmek için sınırlandırılmıştır ve çok hızlı bir geri dönüş olmalıdır (diğer bir şekilde diskin okunması veya kaynak denetim sisteminden durum sorulması gerekir); aksi takdirde IDE'nin performansı bozulmaya başlayabilir.

 Rapor için durum güncelleştirmesi yoksa, kaynak denetimi eklentisi işaret edilen arabellekte boş bir dize `lpFileName`depolar. Aksi takdirde, eklenti durum bilgilerinin değiştiği dosyanın tam yol adını depolar ve uygun durum kodunu döndürür [(Dosya durum kodunda](../extensibility/file-status-code-enumerator.md)ayrıntılı değerlerden biri).

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak kontrol eklentisi API fonksiyonları](../extensibility/source-control-plug-in-api-functions.md)
- [Dosya durum kodu](../extensibility/file-status-code-enumerator.md)
