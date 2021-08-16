---
description: Bu işlev, kaynak denetimi altında bir dizi seçili dosya için durum bilgilerini edinir.
title: SccQueryInfo Işlevi | Microsoft Docs
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
ms.openlocfilehash: 6bc71134c1f0f6040f99ce31d757fade5aef649318a08ede79898dd757d6b4bb
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121414096"
---
# <a name="sccqueryinfo-function"></a>SccQueryInfo İşlevi
Bu işlev, kaynak denetimi altında bir dizi seçili dosya için durum bilgilerini edinir.

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

'ndaki Kaynak denetimi eklentisi bağlam yapısı.

 Nkarşıya

'ndaki Dizide belirtilen dosya sayısı `lpFileNames` ve `lpStatus` dizinin uzunluğu.

 lpDosyaAdı

'ndaki Sorgulanacak dosyaların bir dizi adı.

 lpStatus

[in, out] Kaynak denetimi eklentisinin her dosya için durum bayraklarını döndürdüğü bir dizi. Daha fazla bilgi için bkz. [dosya durum kodu](../extensibility/file-status-code-enumerator.md).

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Sorgu başarılı oldu.|
|SCC_E_ACCESSFAILURE|Büyük olasılıkla ağ veya çekişme sorunlarından kaynaklanan kaynak denetim sistemine erişirken bir sorun oluştu. Yeniden deneme önerilir.|
|SCC_E_PROJNOTOPEN|Proje, kaynak denetimi altında açık değil.|
|SCC_E_NONSPECIFICERROR|Özel olmayan hata.|

## <a name="remarks"></a>Açıklamalar
 `lpFileName`Boş bir dize ise, şu anda güncelleştirilecek durum bilgisi yoktur. Aksi takdirde, durum bilgisinin değiştiği dosyanın tam yolu adıdır.

 Dönüş dizisi bir bit bit maskesi olabilir `SCC_STATUS_xxxx` . Daha fazla bilgi için bkz. [dosya durum kodu](../extensibility/file-status-code-enumerator.md). Kaynak denetim sistemi, tüm bit türlerini desteklemeyebilir. Örneğin `SCC_STATUS_OUTOFDATE` önerilmeyecekse, bit yalnızca ayarlı değildir.

 Dosyaları kullanıma almak için bu işlevi kullanırken aşağıdaki durum gereksinimlerine göz atın `MSSCCI` :

- `SCC_STATUS_OUTBYUSER` Geçerli Kullanıcı dosyayı kullanıma almışsa ayarlanır.

- `SCC_STATUS_CHECKEDOUT` ayarlanmadığı takdirde ayarlanamaz `SCC_STATUS_OUTBYUSER` .

- `SCC_STATUS_CHECKEDOUT` yalnızca dosya belirtilen çalışma dizinine teslim edildiğinde ayarlanır.

- Dosya geçerli kullanıcı tarafından, çalışma dizininden farklı bir dizine teslim edildiğinde, `SCC_STATUS_OUTBYUSER` ayarlanır ancak `SCC_STATUS_CHECKEDOUT` değildir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [Dosya Durumu Kodu](../extensibility/file-status-code-enumerator.md)
