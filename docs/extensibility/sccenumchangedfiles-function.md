---
description: Yerel dosyaların listesini verilen bu işlev, hangi dosyaların kaynak kod denetimi veritabanındaki karşılık gelen sürümlerden farklı olduğunu belirler.
title: SccEnumChangedFiles İşlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2b0707c049013fd3a0272d1f024e4fdbc342bab1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904545"
---
# <a name="sccenumchangedfiles-function"></a>SccEnumChangedFiles işlevi
Yerel dosyaların listesini verilen bu işlev, hangi dosyaların kaynak kod denetimi veritabanındaki karşılık gelen sürümlerden farklı olduğunu belirler.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccEnumChangedFiles(
   LPVOID  pContext,
   HWND    hWnd,
   LONG    cFiles,
   LPCSTR* lpFileNames,
   LONG*   plIsFileDifferent
);
```

### <a name="parameters"></a>Parametreler
 Pcontext

[in] Kaynak denetimi eklentisi bağlam işaretçisi.

 Hwnd

[in] Kaynak denetimi eklentisinin sağladığı iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi tanıtıcısı.

 cFiles

[in] Dizide belirtilen dosya adı `lpFileNames` sayısı. Ayrıca dizinin boyutunu `plIsFileDifferent` belirtir.

 lpFileNames

[in] Kontrol etmek için yerel dosya adları dizisi.

 plIsFileDifferent

[in, out] Her dosyanın fark durumunu gösteren değer dizisi (dizi en az `cFiles` girişlere sahip olmalı). Sıfır olmayan, dosyanın farklı olduğu anlamına gelir.

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetimi eklentisinin aşağıdaki değerlerden birini dönmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|İşlem başarıyla tamamlandı.|
|SCC_UNSPECIFIEDERROR|Genel hata.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)
