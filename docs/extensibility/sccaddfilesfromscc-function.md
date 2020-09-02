---
title: SccAddFilesFromSCC Işlevi | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701283"
---
# <a name="sccaddfilesfromscc-function"></a>SccAddFilesFromSCC işlevi
Bu işlev, kaynak denetiminden açık olan projeye bir dosya listesi ekler.

## <a name="syntax"></a>Söz dizimi

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
 pContext

'ndaki Kaynak denetimi eklentisi bağlam işaretçisi.

 lendiği

'ndaki Kaynak denetimi eklentisinin, sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi için bir işleyici.

 lpUser

[in, out] Kullanıcı adı (en fazla SCC_USER_SIZE, null Sonlandırıcı dahil).

 lpAuxProjPath

[in, out] Projeyi tanımlayan yardımcı dize ( `SCC_PRJPATH_` null Sonlandırıcı dahil olmak üzere).

 cFiles

'ndaki Tarafından verilen dosya sayısı `lpFilePaths` .

 lpFilePaths

[in, out] Geçerli projeye eklenecek dosya adları dizisi.

 lpDestination

'ndaki Dosyaların yazılacağı hedef yol.

 lpComment açıklaması

'ndaki Eklenmekte olan her bir dosyaya uygulanacak yorum.

 pbResults

[in, out] Her dosya için başarı (sıfır olmayan veya doğru) veya hata (sıfır veya yanlış) göstermek için ayarlanan bayrakların dizisi (dizinin boyutu en az bir olmalıdır `cFiles` ).

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_E_PROJNOTOPEN|Proje açık değil.|
|SCC_E_OPNOTPERFORMED|Bağlantı, tarafından belirtilen projede değil `lpAuxProjPath.`|
|SCC_E_NOTAUTHORIZED|Kullanıcının veritabanını güncelleştirme yetkisi yok.|
|SCC_E_NONSPECIFICERROR|Bilinmeyen hata.|
|SCC_I_RELOADFILE|Bir dosya veya projenin yeniden yüklenmesi gerekiyor.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)
