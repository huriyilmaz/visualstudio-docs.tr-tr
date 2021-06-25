---
description: Bu işlev, geçerli durumları için tam dizinlerin listesini inceler.
title: SccDirQueryInfo İşlev | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9a3e65fa03c7fc2b6a8ce83ba2bb39250547aadb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904623"
---
# <a name="sccdirqueryinfo-function"></a>SccDirQueryInfo işlevi
Bu işlev, geçerli durumları için tam dizinlerin listesini inceler.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccDirQueryInfo(
LPVOID  pContext,
LONG    nDirs,
LPCSTR* lpDirNames,
LPLONG  lpStatus
);
```

### <a name="parameters"></a>Parametreler
 Pcontext

[in] Kaynak denetimi eklentisi bağlam yapısı.

 nDirs

[in] Sorgu için seçilen dizin sayısı.

 lpDirNames

[in] Sorgulanan dizinlerin tam yolları dizisi.

 lpStatus

[in, out] Durum bayraklarını iade etmek için kaynak denetimi eklentisinin dizi yapısı (ayrıntılar [için bkz. Dizin durum](../extensibility/directory-status-code-enumerator.md) kodu).

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetimi eklentisinin aşağıdaki değerlerden birini dönmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Sorgu başarılı oldu.|
|SCC_E_OPNOTSUPPORTED|Kaynak kodu denetim sistemi bu işlemi desteklemez.|
|SCC_E_ACCESSFAILURE|Büyük olasılıkla ağ veya sorun sorun nedeniyle kaynak denetim sistemine erişilirken bir sorun vardı. Yeniden deneme önerilir.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Belirtilmeyen hata.|

## <a name="remarks"></a>Açıklamalar
 işlevi, dönüş dizisini aileden bit maskesiyle doldurur (bkz. Dizin durum kodu), verilen her dizin `SCC_DIRSTATUS` için bir giriş. [](../extensibility/directory-status-code-enumerator.md) Durum dizisi çağıranı tarafından ayrılır.

 IDE, bir dizin yeniden adlandırılamadan önce bu işlevi kullanarak ilgili projeye sahip olup olmadığını sorgular ve dizinin kaynak denetimi altında olup olmadığını kontrol edin. Dizin kaynak denetimi altında yoksa, IDE kullanıcıya doğru uyarıyı sağlar.

> [!NOTE]
> Kaynak denetimi eklentisi durum değerlerinden birini veya daha fazlasını uygulamamayı seçerse, uygulanmamış bitler sıfır olarak ayarlanır.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [Dizin durum kodu](../extensibility/directory-status-code-enumerator.md)
