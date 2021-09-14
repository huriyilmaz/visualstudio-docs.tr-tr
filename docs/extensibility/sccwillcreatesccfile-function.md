---
description: Bu işlev, kaynak denetimi eklentisinin MSSCCPRJ'nin oluşturulmasını destekleyip destekleme olmadığını belirler. Verilen dosyaların her biri için SCC dosyası.
title: SccWillCreateSccFile İşlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ef42e88426f5fa91fcebc5e8ffc1b0954c6554ee
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634502"
---
# <a name="sccwillcreatesccfile-function"></a>SccWillCreateSccFile İşlevi
Bu işlev, kaynak denetimi eklentisinin MSSCCPRJ'nin oluşturulmasını destekleyip destekleme olmadığını belirler. Verilen dosyaların her biri için SCC dosyası.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccWillCreateSccFile(
   LPVOID  pContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LPBOOL  pbSccFiles
);
```

#### <a name="parameters"></a>Parametreler
 Pcontext

[in] Kaynak denetimi eklentisi bağlam işaretçisi.

 nFiles

[in] Diziye dahil edilen dosya `lpFileNames` adlarının sayısı ve dizinin `pbSccFiles` uzunluğu.

 lpFileNames

[in] Kontrol edilecek tam dosya adları dizisi (dizi, çağıranın tarafından ayrılmış olması gerekir).

 pbSccFiles

[in, out] Sonuçların depolandırılı olduğu dizi.

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetimi eklentisinin aşağıdaki değerlerden birini dönmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Başarılı.|
|SCC_E_INVALIDFILEPATH|Dizide yollardan biri geçersiz.|
|SCC_E_NONSPECIFICERROR|Belirtilmeyen hata.|

## <a name="remarks"></a>Açıklamalar
 Bu işlev, kaynak denetim eklentisinin MSSCCPRJ'de destek sağladığını belirlemek için dosya listesiyle çağrılır. Verilen dosyaların her biri için SCC dosyası (MSSCCPRJ hakkında daha fazla bilgi için. SCC dosyası, bkz. [MSSCCPRJ. SCC Dosyası](../extensibility/mssccprj-scc-file.md)). Kaynak denetimi eklentileri MSSCCPRJ oluşturma özelliğine sahip olup olmadığını bildireblir. Başlatma sırasında bildirerek SCC `SCC_CAP_SCCFILE` dosyaları. Eklenti, verilen `TRUE` dosyalardan `FALSE` hangilerinin MSSCCPRJ'ye sahip olduğunu belirtmek için dizide dosya `pbSccFiles` başına veya döndürür. SCC desteği. Eklenti işlevden bir başarı kodu döndürürse, dönüş dizisinde değerlere izin verir. Hata durumunda dizi yoksayılır.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [MSSCCPRJ.SCC Dosyası](../extensibility/mssccprj-scc-file.md)
