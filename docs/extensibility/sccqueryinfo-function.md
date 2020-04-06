---
title: SccQueryInfo Fonksiyonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1efae18f15588f4dacf3409ea95e30af05397c6e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700476"
---
# <a name="sccqueryinfo-function"></a>SccQueryInfo İşlevi
Bu işlev, kaynak denetimi altında seçili dosya kümesi için durum bilgilerini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccQueryInfo(
   LPVOID  pvContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LPLONG  lpStatus
);
```

#### <a name="parameters"></a>Parametreler
 pvContext

[içinde] Kaynak denetimi eklentisi bağlam yapısı.

 nDosyalar

[içinde] `lpFileNames` Dizide belirtilen dosya sayısı ve `lpStatus` dizinin uzunluğu.

 lpFileNames

[içinde] Sorgulanacak bir dizi dosya adı.

 lpDurum

[içinde, dışarı] Kaynak denetimi eklentisinin her dosya için durum bayraklarını döndürdettiği bir dizi. Daha fazla bilgi için [Dosya Durum Kodu'na](../extensibility/file-status-code-enumerator.md)bakın.

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetim eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Sorgu başarılı oldu.|
|SCC_E_ACCESSFAILURE|Kaynak denetim sistemine erişimde büyük olasılıkla ağ veya çekişme sorunları nedeniyle bir sorun vardı. Yeniden deneme önerilir.|
|SCC_E_PROJNOTOPEN|Proje kaynak denetimi altında açık değil.|
|SCC_E_NONSPECIFICERROR|Nonspesifik bir hata.|

## <a name="remarks"></a>Açıklamalar
 Boş `lpFileName` bir dize ise, şu anda güncelleştirilen durum bilgisi yok. Aksi takdirde, durum bilgilerinin değişebileceği dosyanın tam yol adıdır.

 İade dizisi `SCC_STATUS_xxxx` bit maskesi olabilir. Daha fazla bilgi için [Dosya Durum Kodu'na](../extensibility/file-status-code-enumerator.md)bakın. Kaynak denetim sistemi tüm bit türlerini desteklemeyebilir. Örneğin, teklif `SCC_STATUS_OUTOFDATE` edilmezse, bit ayarlanmaz.

 Dosyaları kullanıma almak için bu işlevi `MSSCCI` kullanırken aşağıdaki durum gereksinimlerine dikkat edin:

- `SCC_STATUS_OUTBYUSER`geçerli kullanıcı dosyayı kullanıma aldığında ayarlanır.

- `SCC_STATUS_CHECKEDOUT`ayarlmadığı `SCC_STATUS_OUTBYUSER` sürece ayarlanamaz.

- `SCC_STATUS_CHECKEDOUT`yalnızca dosya belirlenen çalışma dizinine kullanıma alındığunda ayarlanır.

- Dosya, geçerli kullanıcı tarafından çalışma dizininin dışındaki bir dizine ayrılmışsa, `SCC_STATUS_OUTBYUSER` `SCC_STATUS_CHECKEDOUT` ayarlanır, ancak kullanıma alınmaz.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [Dosya Durumu Kodu](../extensibility/file-status-code-enumerator.md)
