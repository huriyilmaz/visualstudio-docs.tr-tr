---
title: SccWillCreateSccDosya Fonksiyonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0694fd6b4ba82faf8b05354765fc5734efe2ef4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700207"
---
# <a name="sccwillcreatesccfile-function"></a>SccWillCreateSccFile İşlevi
Bu işlev, kaynak denetim eklentisinin MSSCCPRJ oluşturulmasını destekleyip desteklemediğini belirler. Verilen dosyaların her biri için SCC dosyası.

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

[içinde] Kaynak denetimi eklentibağlam işaretçisi.

 nDosyalar

[içinde] `lpFileNames` Dizide yer alan dosya adlarının sayısı ve `pbSccFiles` dizinin uzunluğu.

 lpFileNames

[içinde] Denetlenecek tam nitelikli dosya adları dizisi (dizi arayan tarafından tahsis edilmelidir).

 pbSccDosyalar

[içinde, dışarı] Sonuçları depolamak için dizi.

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetim eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Başarılı.|
|SCC_E_INVALIDFILEPATH|Dizideki yollardan biri geçersizdir.|
|SCC_E_NONSPECIFICERROR|Nonspesifik bir hata.|

## <a name="remarks"></a>Açıklamalar
 Bu işlev, kaynak denetim eklentisinin MSSCCPRJ'de destek sağp sağlamamasını belirlemek için dosyaların listesiyle birlikte çağrılır. Verilen dosyaların her biri için SCC dosyası (MSSCCPRJ hakkında daha fazla bilgi için. SCC dosyası, [bkz. SCC Dosyası](../extensibility/mssccprj-scc-file.md)). Kaynak denetimi eklentileri, MSSCCPRJ oluşturma yeteneğine sahip olup olmadıklarını bildirebilir. SCC dosyaları başlatma `SCC_CAP_SCCFILE` sırasında beyan ederek. Verilen dosyalardan `TRUE` hangisinde MSSCCPRJ olduğunu belirtmek için eklenti `FALSE` `pbSccFiles` döndürür veya dizideki dosya başına döner. SCC desteği. Eklenti işlevden bir başarı kodu döndürürse, iade dizisindeki değerler onurlanır. Hatada, dizi yoksayılır.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [MSSCCPRJ.SCC Dosyası](../extensibility/mssccprj-scc-file.md)
