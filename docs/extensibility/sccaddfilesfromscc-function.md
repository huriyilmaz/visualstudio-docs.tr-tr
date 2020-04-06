---
title: SccAddFilesFromSCC Fonksiyonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d22527644edbf1697112f5cf8b73b8a3f72b774
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701283"
---
# <a name="sccaddfilesfromscc-function"></a>SccAddFilesFromSCC fonksiyonu
Bu işlev, kaynak denetiminden şu anda açılan projeye dosyaların bir listesini ekler.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccAddFilesFromSCC(
   LPVOID  pContext,
   HWND    hWnd,
   LPSTR   lpUser,
   LPSTR   lpAuxProjPath,
   LONG    cFiles,
   LPCSTR* lpFilePaths,
   LPCSTR  lpDestination,
   LPCSTR  lpComment,
   LPBOOL  pbResults
);
```

### <a name="parameters"></a>Parametreler
 Pcontext

[içinde] Kaynak denetimi eklentibağlam işaretçisi.

 Hwnd

[içinde] Kaynak denetim eklentisinin sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresine bir tanıtıcı.

 lpUser

[içinde, dışarı] Kullanıcı adı (null terminator dahil SCC_USER_SIZE kadar).

 lpAuxProjPath

[içinde, dışarı] Projeyi tanımlayan yardımcı dize `SCC_PRJPATH_`(null terminator dahil olmak üzere SIZE'a kadar).

 cDosyalar

[içinde] Tarafından `lpFilePaths`verilen dosya sayısı.

 lpFilePaths

[içinde, dışarı] Geçerli projeye eklenecek dosya adları dizisi.

 lpDestination

[içinde] Dosyaların yazılabilmek için hedef yolu.

 lpYorum yap

[içinde] Eklenen dosyaların her birine uygulanacak açıklama.

 pbSonuçlar

[içinde, dışarı] Her dosya için başarı (sıfır olmayan veya DOĞRU olmayan) veya hata (sıfır veya FALSE) gösterecek `cFiles` şekilde ayarlanmış bayraklar dizisi (dizinin boyutu en az uzun olmalıdır).

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetim eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_E_PROJNOTOPEN|Proje açık değil.|
|SCC_E_OPNOTPERFORMED|Bağlantı tarafından belirtilen aynı proje değil`lpAuxProjPath.`|
|SCC_E_NOTAUTHORIZED|Kullanıcının veritabanını güncelleştirme yetkisi yoktur.|
|SCC_E_NONSPECIFICERROR|Bilinmeyen hata.|
|SCC_I_RELOADFILE|Bir dosyanın veya projenin yeniden yüklenmesi gerekir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak kontrol eklentisi API fonksiyonları](../extensibility/source-control-plug-in-api-functions.md)
