---
title: SccQueryChanges Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 617f07a11f92ab65f079c7d1b41773494e3d0c8b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720861"
---
# <a name="sccquerychanges-function"></a>SccQueryChanges İşlevi
Bu işlev, bir geri çağırma işlevi aracılığıyla her bir dosya için ad değişiklikleri hakkında bilgi sağlayan belirli bir dosya listesini numaralandırır.

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
 pContext

'ndaki Kaynak denetimi eklentisi bağlam işaretçisi.

 Nkarşıya

'ndaki @No__t_0 dizisindeki dosya sayısı.

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