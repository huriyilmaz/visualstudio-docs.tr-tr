---
title: SccGetEvents Işlevi | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700814"
---
# <a name="sccgetevents-function"></a>SccGetEvents işlevi
Bu işlev, bir sıraya alınmış durum olayını alır.

## <a name="syntax"></a>Söz dizimi

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

'ndaki Kaynak denetimi eklentisi bağlam yapısı.

 lpFileName

[in, out] Kaynak denetimi eklentisinin döndürülen dosya adını (_MAX_PATH karaktere kadar) yerleştirme arabelleği.

 lpStatus

[in, out] Durum kodunu döndürür (olası değerler için [dosya durum koduna](../extensibility/file-status-code-enumerator.md) bakın).

 Pneventskaldı

[in, out] Bu çağrıdan sonra sırada kalan giriş sayısını döndürür. Bu sayı büyükse, çağıran tüm bilgileri bir kerede almak için [SccQueryInfo](../extensibility/sccqueryinfo-function.md) çağrısına karar verebilir.

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Olayları başarılı bir şekilde alın.|
|SCC_E_OPNOTSUPPORTED|Bu işlev desteklenmiyor.|
|SCC_E_NONSPECIFICERROR|Özel olmayan hata.|

## <a name="remarks"></a>Açıklamalar
 Bu işlev, kaynak denetimi altındaki dosyalar için herhangi bir durum güncelleştirmesi olup olmadığını görmek için boşta işleme sırasında çağrılır. Kaynak denetimi eklentisi, bildiği tüm dosyaların durumunu korur ve eklenti tarafından bir durum değişikliği olduğunda, durum ve ilişkili dosya bir kuyrukta depolanır. `SccGetEvents`Çağrıldığında, sıranın üst öğesi alınır ve döndürülür. Bu işlev, yalnızca daha önce önbelleğe alınmış bilgileri döndürecek şekilde kısıtlıdır ve çok hızlı bir şekilde (disk okuma veya kaynak denetim sistemine durum sorma) sahip olmalıdır; Aksi takdirde IDE 'nin performansı azalmayı başlatabilir.

 Raporlanacak durum güncelleştirmesi yoksa, kaynak denetimi eklentisi tarafından işaret edilen arabellekte boş bir dize depolar `lpFileName` . Aksi halde eklenti, durum bilgisinin değiştiği dosyanın tam yol adını depolar ve uygun durum kodunu ( [dosya durum kodunda](../extensibility/file-status-code-enumerator.md)ayrıntılanmış değerlerden biri) döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [Dosya durum kodu](../extensibility/file-status-code-enumerator.md)
