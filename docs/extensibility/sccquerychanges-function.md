---
description: Bu işlev, bir geri çağırma işlevi aracılığıyla her dosya için ad değişiklikleri hakkında bilgi sağlayarak, verilen dosya listesini numaralar.
title: SccQueryChanges İşlev | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: aaec646a190dc8b1f30d585b491803b06443a8fe
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122109987"
---
# <a name="sccquerychanges-function"></a>SccQueryChanges İşlevi
Bu işlev, bir geri çağırma işlevi aracılığıyla her dosya için ad değişiklikleri hakkında bilgi sağlayarak, verilen dosya listesini numaralar.

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
 Pcontext

[in] Kaynak denetimi eklentisi bağlam işaretçisi.

 nFiles

[in] Dizide dosya `lpFileNames` sayısı.

 lpFileNames

[in] Hakkında bilgi almak için dosya adları dizisi.

 pfnCallback

[in] Listede her dosya adı için çağrı yapmak için geri çağırma işlevi (ayrıntılar [için bkz. QUERYCHANGESFUNC).](../extensibility/querychangesfunc.md)

 pvCallerData

[in] Değiştirilmeden geri çağırma işlevine geçirilecek değer.

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetimi eklentisinin aşağıdaki değerlerden birini dönmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Sorgu işlemi başarıyla tamamlandı.|
|SCC_E_PROJNOTOPEN|Proje kaynak denetiminde açık değil.|
|SCC_E_ACCESSFAILURE|Kaynak denetim sistemine erişirken büyük olasılıkla ağ veya iletişim sorunları nedeniyle bir sorun vardı.|
|SCC_E_NONSPECIFICERROR|Belirtilmemiş veya genel bir hata oluştu.|

## <a name="remarks"></a>Açıklamalar
 Sorgulanan değişiklikler ad alanıdır: özellikle bir dosyayı yeniden adlandırma, ekleme ve kaldırma.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)
- [Hata Kodları](../extensibility/error-codes.md)
