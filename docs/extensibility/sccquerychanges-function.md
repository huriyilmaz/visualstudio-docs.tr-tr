---
description: Bu işlev, bir geri çağırma işlevi aracılığıyla her bir dosya için ad değişiklikleri hakkında bilgi sağlayan belirli bir dosya listesini numaralandırır.
title: SccQueryChanges Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e34c37ca999b05e7148d910032fe90c33470ce50
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102220527"
---
# <a name="sccquerychanges-function"></a>SccQueryChanges İşlevi
Bu işlev, bir geri çağırma işlevi aracılığıyla her bir dosya için ad değişiklikleri hakkında bilgi sağlayan belirli bir dosya listesini numaralandırır.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccQueryChanges(
   LPVOID           pContext,
   LONG             nFiles,
   LPCSTR*          lpFileNames,
   QUERYCHANGESFUNC pfnCallback,
   LPVOID           pvCallerData
);
```

#### <a name="parameters"></a>Parametreler
 pContext

'ndaki Kaynak denetimi eklentisi bağlam işaretçisi.

 Nkarşıya

'ndaki Dizideki dosya sayısı `lpFileNames` .

 lpDosyaAdı

'ndaki Hakkında bilgi almak için dosya adları dizisi.

 pfnCallback

'ndaki Listedeki her dosya adı için çağrı yapılacak geri çağırma işlevi (Ayrıntılar için bkz. [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) ).

 pvCallerData

'ndaki Geri çağırma işlevine değiştirilmeden geçirilecek değer.

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Sorgu işlemi başarıyla tamamlandı.|
|SCC_E_PROJNOTOPEN|Proje kaynak denetiminde açılmadı.|
|SCC_E_ACCESSFAILURE|Büyük olasılıkla ağ veya çekişme sorunlarından dolayı kaynak denetim sistemine erişirken bir sorun oluştu.|
|SCC_E_NONSPECIFICERROR|Belirtilmeyen veya genel bir hata oluştu.|

## <a name="remarks"></a>Açıklamalar
 İçin sorgulanmakta olan değişiklikler ad alanı: özel olarak, bir dosyayı yeniden adlandırma, ekleme ve kaldırma.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)
- [Hata Kodları](../extensibility/error-codes.md)
