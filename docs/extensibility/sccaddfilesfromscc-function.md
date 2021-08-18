---
description: Bu işlev, kaynak denetiminden açık olan projeye dosya listesi ekler.
title: SccAddFilesFromSCC İşlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c8d8715f18d68c6e8f3250f25e14a45da48ab8cd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122144710"
---
# <a name="sccaddfilesfromscc-function"></a>SccAddFilesFromSCC işlevi
Bu işlev, kaynak denetiminden açık olan projeye dosya listesi ekler.

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

[in] Kaynak denetimi eklentisi bağlam işaretçisi.

 Hwnd

[in] Kaynak denetimi eklentisinin sağladığı iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi tanıtıcısı.

 lpUser

[in, out] Kullanıcı adı (null SCC_USER_SIZE kadar).

 lpUxProjPath

[in, out] Projeyi tanımlayan yardımcı dize (null sonlandırıcı `SCC_PRJPATH_` dahil olmak üzere SIZE'a kadar).

 cFiles

[in] tarafından verilen dosya `lpFilePaths` sayısı.

 lpFilePaths

[in, out] Geçerli projeye eklemek için dosya adları dizisi.

 lpDestination

[in] Dosyaların yazıldığı hedef yol.

 lpComment

[in] Eklenecek dosyaların her biri için uygulanacak açıklama.

 pbResults

[in, out] Her dosya için başarı (sıfır olmayan veya TRUE) veya hata (sıfır veya FALSE) belirtmek için ayarlanmış bayrak dizisi (dizinin boyutu en az uzun `cFiles` olmalıdır).

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetimi eklentisinin aşağıdaki değerlerden birini geri dönmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_E_PROJNOTOPEN|Project açık değil.|
|SCC_E_OPNOTPERFORMED|Bağlantı, tarafından belirtilen projeyle aynı değil `lpAuxProjPath.`|
|SCC_E_NOTAUTHORIZED|Kullanıcının veritabanını güncelleştirme yetkisi yok.|
|SCC_E_NONSPECIFICERROR|Bilinmeyen hata.|
|SCC_I_RELOADFILE|Bir dosyanın veya projenin yeniden yüklenmiş olması gerekir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)
