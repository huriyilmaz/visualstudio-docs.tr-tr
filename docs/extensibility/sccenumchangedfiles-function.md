---
title: SccEnumChangedFiles Fonksiyonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b1826a87b20d6bc92254fc4a86b8e0b756400ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700912"
---
# <a name="sccenumchangedfiles-function"></a>SccEnumChangedFiles fonksiyonu
Yerel dosyaların listesi göz önüne alındığında, bu işlev hangi dosyaların kaynak kodu denetim veritabanındaki ilgili sürümlerden farklı olduğunu belirler.

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

[içinde] Kaynak denetimi eklentibağlam işaretçisi.

 Hwnd

[içinde] Kaynak denetim eklentisinin sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresine bir tanıtıcı.

 cDosyalar

[içinde] `lpFileNames` Dizide belirtilen dosya adlarının sayısı. Ayrıca `plIsFileDifferent` dizinin boyutunu belirtir.

 lpFileNames

[içinde] Denetlemek için yerel dosya adları dizisi.

 plIsFileDifferent

[içinde, dışarı] Her dosyanın fark durumunu gösteren değerler dizisi (dizi `cFiles` en az girişleri olmalıdır). Nonzero, dosyanın farklı olduğu anlamına gelir.

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetim eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|İşlem başarıyla tamamlandı.|
|SCC_UNSPECIFIEDERROR|Genel hata.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak kontrol eklentisi API fonksiyonları](../extensibility/source-control-plug-in-api-functions.md)
