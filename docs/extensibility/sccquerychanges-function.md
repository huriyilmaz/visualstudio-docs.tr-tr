---
title: SccQueryChanges Fonksiyonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ec335d808c287decb75bf759d5a3795d98962579
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700490"
---
# <a name="sccquerychanges-function"></a>SccQueryChanges İşlevi
Bu işlev, bir geri arama işlevi aracılığıyla her dosya için ad değişiklikleri hakkında bilgi sağlayarak belirli bir dosya listesini listeler.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccQueryChanges(
   LPVOID           pContext,
   LONG             nFiles,
   LPCSTR*          lpFileNames,
   QUERYCHANGESFUNC pfnCallback,
   LPVOID           pvCallerData
);
```

#### <a name="parameters"></a>Parametreler
 Pcontext

[içinde] Kaynak denetimi eklentibağlam işaretçisi.

 nDosyalar

[içinde] Dizideki `lpFileNames` dosya sayısı.

 lpFileNames

[içinde] Hakkında bilgi almak için dosya adları dizisi.

 pfnCallback

[içinde] Listedeki her dosya adı için çağrı yapmak için geri arama işlevi (ayrıntılar için [QUERYCHANGESFUNC'a](../extensibility/querychangesfunc.md) bakın).

 pvCallerData

[içinde] Geri arama işlevine değişmeden geçirilecek değer.

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetim eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Sorgu işlemi başarıyla tamamlandı.|
|SCC_E_PROJNOTOPEN|Proje kaynak denetiminde açılmadı.|
|SCC_E_ACCESSFAILURE|Kaynak denetim sistemine erişmede büyük olasılıkla ağ veya çekişme sorunları nedeniyle bir sorun vardı.|
|SCC_E_NONSPECIFICERROR|Belirtilmeyen veya genel bir hata oluştu.|

## <a name="remarks"></a>Açıklamalar
 Sorgulanan değişiklikler ad alanındadır: özellikle, bir dosyayı yeniden adlandırma, ekleme ve kaldırma.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)
- [Hata Kodları](../extensibility/error-codes.md)
