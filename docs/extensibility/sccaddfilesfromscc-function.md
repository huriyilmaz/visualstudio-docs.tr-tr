---
description: Bu işlev, kaynak denetiminden açık olan projeye bir dosya listesi ekler.
title: SccAddFilesFromSCC Işlevi | Microsoft Docs
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
ms.workload:
- vssdk
ms.openlocfilehash: 6fa08ec93383fa661d1e2dd055b3139b2ba90f34
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904876"
---
# <a name="sccaddfilesfromscc-function"></a>SccAddFilesFromSCC işlevi
Bu işlev, kaynak denetiminden açık olan projeye bir dosya listesi ekler.

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
