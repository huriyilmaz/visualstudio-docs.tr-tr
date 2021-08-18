---
description: Bu işlev, kaynak denetimi altındaki bir dizi seçili dosyanın durum bilgilerini elde ediyor.
title: SccQueryInfo İşlev | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 7b61a5cfd52bfbeadf2b11212bd3f215390d2d4d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122110013"
---
# <a name="sccqueryinfo-function"></a>SccQueryInfo İşlevi
Bu işlev, kaynak denetimi altındaki bir dizi seçili dosyanın durum bilgilerini elde ediyor.

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

[in] Kaynak denetimi eklentisi bağlam yapısı.

 nFiles

[in] Dizide belirtilen dosya `lpFileNames` sayısı ve dizinin `lpStatus` uzunluğu.

 lpFileNames

[in] Sorgulanan dosyaların adları dizisi.

 lpStatus

[in, out] Kaynak denetimi eklentisinin her dosya için durum bayraklarını döndüren bir dizi. Daha fazla bilgi için [bkz. Dosya Durumu Kodu.](../extensibility/file-status-code-enumerator.md)

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetimi eklentisinin aşağıdaki değerlerden birini geri dönmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Sorgu başarılı oldu.|
|SCC_E_ACCESSFAILURE|Kaynak denetim sistemine erişimle ilgili bir sorun vardı, bunun nedeni büyük olasılıkla ağ veya iletişim sorunlarıdır. Yeniden deneme önerilir.|
|SCC_E_PROJNOTOPEN|Proje kaynak denetimi altında açık değil.|
|SCC_E_NONSPECIFICERROR|Belirtilmeyen hata.|

## <a name="remarks"></a>Açıklamalar
 boş `lpFileName` bir dize ise, şu anda güncelleştirilen bir durum bilgisi yoktur. Aksi takdirde, durum bilgisinin değişmiş olduğu dosyanın tam yol adıdır.

 Dönüş dizisi bit maskesi `SCC_STATUS_xxxx` olabilir. Daha fazla bilgi için [bkz. Dosya Durumu Kodu.](../extensibility/file-status-code-enumerator.md) Kaynak denetim sistemi tüm bit türlerini desteklemez. Örneğin, `SCC_STATUS_OUTOFDATE` sunlanmazsa bit ayarlanmaz.

 Dosyaları kontrol etmek için bu işlevi kullanırken aşağıdaki durum gereksinimlerine `MSSCCI` dikkat edin:

- `SCC_STATUS_OUTBYUSER` , geçerli kullanıcı dosyayı kullanıma alınmış olduğunda ayarlanır.

- `SCC_STATUS_CHECKEDOUT` ayar olmadığı sürece `SCC_STATUS_OUTBYUSER` ayar olamaz.

- `SCC_STATUS_CHECKEDOUT` yalnızca dosya belirlenen çalışma dizinine kullanıma alınmış olduğunda ayarlanır.

- Dosya, geçerli kullanıcı tarafından çalışma dizini dışında bir dizine iade edildi ise ayarlanır ancak `SCC_STATUS_OUTBYUSER` `SCC_STATUS_CHECKEDOUT` ayarlanmaz.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [Dosya Durumu Kodu](../extensibility/file-status-code-enumerator.md)
