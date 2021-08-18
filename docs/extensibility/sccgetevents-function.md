---
description: Bu işlev kuyruğa alınan bir durum olayı döndürür.
title: SccGetEvents İşlev | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 2a5c382b7c7a5bd48d1b2db22a4c0469d0f16b2d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122144450"
---
# <a name="sccgetevents-function"></a>SccGetEvents işlevi
Bu işlev kuyruğa alınan bir durum olayı döndürür.

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

[in] Kaynak denetimi eklentisi bağlam yapısı.

 lpFileName

[in, out] Kaynak denetimi eklentisinin döndürülen dosya adını (en fazla _MAX_PATH koyan) arabelleğe alma.

 lpStatus

[in, out] Durum kodunu döndürür (olası [değerler için bkz.](../extensibility/file-status-code-enumerator.md) Dosya durumu kodu).

 pnEventsRemaining

[in, out] Bu çağrıdan sonra kuyrukta kalan giriş sayısını döndürür. Bu sayı büyükse, çağıranı tüm bilgileri aynı anda almak için [SccQueryInfo'nun](../extensibility/sccqueryinfo-function.md) çağrısını almaya karar verir.

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetimi eklentisinin aşağıdaki değerlerden birini dönmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Get events succeeded.|
|SCC_E_OPNOTSUPPORTED|Bu işlev desteklenmiyor.|
|SCC_E_NONSPECIFICERROR|Belirtilmeyen hata.|

## <a name="remarks"></a>Açıklamalar
 Bu işlev, kaynak denetimi altındaki dosyalar için herhangi bir durum güncelleştirmesi olup bu işlev boşta işlem sırasında çağrılır. Kaynak denetimi eklentisi, bildiği tüm dosyaların durumunu sürdürür ve eklenti tarafından durum değişikliği her not edildi mi, durum ve ilişkili dosya bir kuyrukta depolanır. `SccGetEvents`çağrıldı mı, kuyruğun en üst öğesi alınır ve döndürülür. Bu işlev yalnızca önceden önbelleğe alınmış bilgileri döndüren şekilde kısıtlanmış ve çok hızlı bir geri dönüşe sahip olmalıdır (başka bir ifadeyle diskin okunması veya kaynak denetim sisteminde durum bilgisi sorulmamalıdır); aksi takdirde IDE'nin performansı düşebilir.

 Rapor için durum güncelleştirmesi yoksa, kaynak denetim eklentisi tarafından işaret eden arabellekte boş bir dize `lpFileName` depolar. Aksi takdirde eklenti, durum bilgisinin değiştir olduğu dosyanın tam yol adını depolar ve uygun durum kodunu (Dosya durum kodunda açıklanan değerlerden [biri) döndürür.](../extensibility/file-status-code-enumerator.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [Dosya durumu kodu](../extensibility/file-status-code-enumerator.md)
