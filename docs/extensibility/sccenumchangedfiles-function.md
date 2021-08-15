---
description: Yerel dosyaların listesi verildiğinde, bu işlev kaynak kodu denetim veritabanındaki ilgili sürümlerden farklı olan dosyaları belirler.
title: SccEnumChangedFiles Işlevi | Microsoft Docs
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 500d0072ffca6f0ada6d035aa59c60b8358a13aec9230077b64a724f5faf4747
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121273689"
---
# <a name="sccenumchangedfiles-function"></a>SccEnumChangedFiles işlevi
Yerel dosyaların listesi verildiğinde, bu işlev kaynak kodu denetim veritabanındaki ilgili sürümlerden farklı olan dosyaları belirler.

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
 pContext

'ndaki Kaynak denetimi eklentisi bağlam işaretçisi.

 lendiği

'ndaki Kaynak denetimi eklentisinin, sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi için bir işleyici.

 cFiles

'ndaki Dizide belirtilen dosya adı sayısı `lpFileNames` . Ayrıca dizinin boyutunu belirtir `plIsFileDifferent` .

 lpDosyaAdı

'ndaki Denetlenecek yerel dosya adları dizisi.

 Plisfilefarklı

[in, out] Her dosyanın fark durumunu gösteren değerler dizisi (dizi en az girişe sahip olmalıdır `cFiles` ). Sıfır dışında, dosyanın farklı olduğu anlamına gelir.

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|İşlem başarıyla tamamlandı.|
|SCC_UNSPECIFIEDERROR|Genel hata.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)
