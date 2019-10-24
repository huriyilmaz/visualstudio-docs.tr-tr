---
title: SccQueryInfo Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5807eb6b695e140350696436a8bba351687f4a24
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720826"
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

'ndaki @No__t_0 dizisinde belirtilen dosya sayısı ve `lpStatus` dizisinin uzunluğu.

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
 @No__t_0 boş bir dize ise, şu anda güncelleştirilecek durum bilgisi yoktur. Aksi takdirde, durum bilgisinin değiştiği dosyanın tam yolu adıdır.

 Dönüş dizisi `SCC_STATUS_xxxx` bitlerin bir bit maskesi olabilir. Daha fazla bilgi için bkz. [dosya durum kodu](../extensibility/file-status-code-enumerator.md). Kaynak denetim sistemi, tüm bit türlerini desteklemeyebilir. Örneğin, `SCC_STATUS_OUTOFDATE` sunulmadığı takdirde, bit yalnızca ayarlı değildir.

 Dosyaları kullanıma almak için bu işlevi kullanırken aşağıdaki `MSSCCI` durum gereksinimlerine göz atın:

- `SCC_STATUS_OUTBYUSER`, geçerli kullanıcı dosyayı kullanıma almışsa ayarlanır.

- `SCC_STATUS_OUTBYUSER` ayarlanmadığı müddetçe `SCC_STATUS_CHECKEDOUT` ayarlanamaz.

- `SCC_STATUS_CHECKEDOUT` yalnızca dosya belirtilen çalışma dizinine teslim edildiğinde ayarlanır.

- Dosya geçerli kullanıcı tarafından, çalışma dizininden farklı bir dizine teslim edildiğinde `SCC_STATUS_OUTBYUSER` ayarlanır ancak `SCC_STATUS_CHECKEDOUT` değildir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [Dosya Durumu Kodu](../extensibility/file-status-code-enumerator.md)