---
title: SccWillCreateSccFile Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 50ef18e44579525df136bd770cda96124cb30c87
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956873"
---
# <a name="sccwillcreatesccfile-function"></a>SccWillCreateSccFile İşlevi
Bu işlev, kaynak denetimi eklentisinin MSSCCPRJ oluşturulmasını destekleyip desteklemediğini belirler. Verilen dosyaların her biri için SCC dosyası.

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
 pContext

'ndaki Kaynak denetimi eklentisi bağlam işaretçisi.

 Nkarşıya

'ndaki Diziye dahil edilen dosya adı sayısı ve `lpFileNames` `pbSccFiles` dizinin uzunluğu.

 lpDosyaAdı

'ndaki Denetlenecek tam dosya adları dizisi (dizi arayan tarafından ayrılmalıdır).

 pbSccFiles

[in, out] Sonuçların kaydedileceği dizi.

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Başarılı.|
|SCC_E_INVALIDFILEPATH|Dizideki yollardan biri geçersiz.|
|SCC_E_NONSPECIFICERROR|Özel olmayan hata.|

## <a name="remarks"></a>Açıklamalar
 Bu işlev, kaynak denetimi eklentisinin MSSCCPRJ 'de destek sağladığını öğrenmek için bir dosya listesi ile çağırılır. Belirli dosyaların her biri için SCC dosyası (MSSCCPRJ hakkında daha fazla bilgi için. SCC dosyası, bkz [. Mssccprj. SCC dosyası](../extensibility/mssccprj-scc-file.md)). Kaynak denetimi eklentileri, MSSCCPRJ oluşturma yeteneğine sahip olup olmadığını bildirebilir. Başlatma sırasında bildirerek SCC dosyaları `SCC_CAP_SCCFILE` . Eklenti, `TRUE` `FALSE` `pbSccFiles` BELIRTILEN dosyalardan hangisinin Mssccprj olduğunu göstermek için dizideki dosya başına veya dosya başına döndürür. SCC desteği. Eklenti işlevinden bir başarı kodu döndürürse, dönüş dizisindeki değerler kabul edilir. Hatada, dizi yok sayılır.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [MSSCCPRJ.SCC Dosyası](../extensibility/mssccprj-scc-file.md)
